# Maintainer: sourav-majumdar-math

# NOTE: If you are experiencing segmentation fault, delete the ".rstudio-desktop" folder from your home directory then restart the program should fix the issue.

pkgname=rstudio-bin
pkgver=2025.05.1.513
_pkgver=2025.05.1-513
pkgrel=1
pkgdesc="An integrated development environment (IDE) for R (binary from RStudio official repository)"
arch=('x86_64')
license=('GPL')
url="http://www.rstudio.org/"
depends=('r>=3.3.0' 'hicolor-icon-theme' 'shared-mime-info' 'openssl'
  'libxkbcommon-x11' 'libedit' 'postgresql-libs' 'sqlite' 'nss')
makedepends=()
optdepends=(
'clang: C/C++ and Rcpp support'
)
conflicts=('rstudio-desktop' 'rstudio-desktop-git' 'rstudio-desktop-preview-bin' 'rstudio-desktop-bin')
provides=("rstudio-desktop=${pkgver}")
options=(!strip)

sha256sums_x86_64=(
89a68b37fc700ff28fea16e3a8771cea58c72d573e3b09cba7f8d3ead74fc58d 
)

source_x86_64=("https://download1.rstudio.org/electron/jammy/amd64/rstudio-${_pkgver}-amd64.deb"
)


install="$pkgname".install

package() {

        shopt -s extglob
 
        msg "Converting debian package..."
 
        cd "$srcdir"
        tar Jxpf data.tar.xz -C "$pkgdir"
        install -dm755 "$pkgdir/usr/bin"
        cd "$pkgdir/usr/bin"
        echo '#!/bin/sh
        export QT_DIR=/usr/lib/rstudio
        export QT_PLUGIN_PATH=$QT_DIR/plugins
        export QT_QPA_PLATFORM_PLUGIN_PATH=$QT_PLUGIN_PATH/platforms
        export KDEDIRS=/usr
        exec /usr/lib/rstudio/rstudio "$@"
        ' > "$pkgdir/usr/bin/rstudio-bin"
                chmod 755 "$pkgdir/usr/bin/rstudio-bin" 
                sed -i 's|/usr/lib/rstudio/rstudio|/usr/bin/rstudio-bin|' "$pkgdir/usr/share/applications/rstudio.desktop"
}
