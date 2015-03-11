# $Id$
# 

pkgname=i3lock
pkgver=2.6
pkgrel=1
pkgdesc="An improved screenlocker based upon XCB and PAM"
arch=('i686' 'x86_64')
url="http://i3wm.org/i3lock/"
license=('MIT')
groups=("i3")
provides=("i3lock")
conflicts=("i3lock")
depends=('xcb-util-image' 'libev' 'cairo' 'libxkbcommon-x11')
options=('docs')
backup=("etc/pam.d/i3lock")
source=("git://github.com/rlbossman/i3lock")
SHA1SUMS=("skip")

_gitname="i3lock"

build() {
	cd "${srcdir}/${pkgname}"

	# Fix ticket FS#31544, sed line taken from gentoo
	sed -i -e 's:login:system-auth:' i3lock.pam

	make
	gzip i3lock.1
}

package() {
	cd "$_gitname"

	make DESTDIR="${pkgdir}" install

	install -Dm644 i3lock.1.gz ${pkgdir}/usr/share/man/man1/i3lock.1.gz
	install -Dm644 LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
	make clean
}

