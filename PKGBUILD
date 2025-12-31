# Maintainer: Frederik Schwan <freswa at archlinux dot org>
# Contributor:Francois Menning <f.menning@pm.me>
# Contributor: gilbus <aur(AT)tinkershell.eu>
# Contributor: Bruno Pagani <archange@archlinux.org>

pkgname=thermald-redmibook
_pkgname=thermal_daemon
epoch=1
pkgver=2.5.11
pkgrel=1
pkgdesc='The Linux Thermal Daemon program from 01.org'
arch=('x86_64')
url='https://github.com/sergoops/thermal_daemon.git'
license=('GPL2')
depends=(
  dbus-glib
  libevdev
  libxml2
  upower
)
makedepends=(
  autoconf-archive
  git
  gtk-doc
  python
)
conflicts=('thermald')
provides=('thermald')
source=(
  "git+https://github.com/sergoops/thermal_daemon.git#tag=v${pkgver}-redmi"
)
b2sums=('12a3cb69896977167ec66c79d729476fb227a37775e865c0187b7cb1b4d0be251fcf6c61b8b9515f301a4803af6af168514e5b14784a2320639fe461595b5ae8')

build() {
  cd ${_pkgname}
  ./autogen.sh
  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --with-dbus-sys-dir=/usr/share/dbus-1/system.d \
    --localstatedir=/var \
    --sbindir=/usr/bin
  make
}

package() {
  cd ${_pkgname}
  DESTDIR="${pkgdir}" make install
}
