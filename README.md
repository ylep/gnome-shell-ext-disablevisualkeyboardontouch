Block the GNOME 3 on-screen keyboard from popping up when you use a touchscreen, even if it's disabled in the accessibility services menu.

Adapted from <https://github.com/keringar/cariboublocker> by <yann.leprince@cea.fr> to work for GNOME Shell 3.28 (Ubuntu 18.04.6).

Workaround for: https://bugzilla.gnome.org/show_bug.cgi?id=742246

# System-wide installation

```shell
DESTDIR=/usr/local/share/gnome-shell/extensions/disablevisualkeyboardontouch@ylep.fr
sudo mkdir -p "$DESTDIR"
sudo cp metadata.json extension.js "$DESTDIR"
cat <<EOF | sudo tee /etc/dconf/db/local.d/10-local-extensions > /dev/null
[org/gnome/shell]
enabled-extensions=['dash-to-dock@micxgx.gmail.com', 'suspend-button@laserb', 'disablevisualkeyboardontouch@ylep.fr']
EOF
sudo dconf update
```
