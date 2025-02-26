# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer: Ivan Fonseca <ivanfon@riseup.net>
# Contributor: Simon Conseil <contact+aur at saimon dot org>
# Contributor: Michael Louis Thaler <michael.louis.thaler@gmail.com>
# Contributor: Mark Harviston infinull@gmail.com
# Contributor: BlackEagle < ike DOT devolder AT gmail DOT com >

_node="nodejs"
_pkg=jslint
pkgname="${_pkg}"
pkgver=0.12.1
pkgrel=1
_pkgdesc=(
  "Easily use JSLint from the command line."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="reid"
url="${_http}/${_ns}/node-jslint"
license=(
  'custom:BSD and modified MIT'
)
depends=(
  "${_node}"
)
makedepends=(
  'npm'
)
provides+=(
  "${_node}-${_pkg}=${pkgver}"
)
_npm="https://registry.npmjs.org"
source=(
  "${_npm}/${_pkg}/-/${_pkg}-${pkgver}.tgz"
)
sha256sums=(
  '47298dd155e0655f3c30fd30ecae68b06fe45210365e8ecf11b1a8e887f5c280'
)

package() {
  local \
    _npm_opts=()
  _npm_opts=(
    -g
    # --user
    #   "root"
    --prefix \
      "${pkgdir}/usr"
  )
  npm \
    install \
    "${_npm_opts[@]}" \
    "${srcdir}/${_pkg}-${pkgver}.tgz"
  # Non-deterministic race in npm gives 777 permissions to random directories.
  # See https://github.com/npm/npm/issues/9359 for details.
  find \
    "${pkgdir}/usr" \
    -type \
      "d" \
    -exec \
      chmod \
        755 \
        {} +
}

# vim:set ts=2 sw=2 et:
