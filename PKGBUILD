# Maintainer: Quint Guvernator <quint@guvernator.net>
pkgname=wg-ui
pkgver=1.3.0
pkgrel=1
pkgdesc="A basic, self-contained management service for WireGuard with a self-serve web UI."
arch=(x86_64)
url="https://github.com/EmbarkStudios/wg-ui"
license=(MIT Apache)
depends=(
    wireguard-tools
)
install=
source=(
	"https://github.com/EmbarkStudios/wg-ui/releases/download/v1.3.0/${pkgname}-${pkgver}-linux-amd64.tar.gz"
    "${pkgname}.service"
	"${pkgname}-${pkgver}::git+https://github.com/EmbarkStudios/wg-ui#tag=v${pkgver}"
)
sha256sums=('6895fe666a42e13b8ccd1aa42254371015e80e73b932074a82de20f6ac5f7cab'
            '2b55c39253a55ae63e6d487a6515cc7e8969ee475723698ac75344b77de97e62'
            'SKIP')

package() {

    # binary
    install -Dm 755 \
		"${pkgname}-${pkgver}-linux-amd64" \
		"${pkgdir}/usr/bin/${pkgname}"

    # systemd service
    install -Dm 600 \
		"${pkgname}.service" \
		-t "${pkgdir}/usr/lib/systemd/system"

    # docs
    cd "$pkgname-$pkgver"
	install -Dm 644 \
		CHANGELOG.md \
		README.md \
		CODE_OF_CONDUCT.md \
		-t "${pkgdir}/usr/share/doc/${pkgname}"
}
