---
title: "Where'd Epiphany go?"
date: 2008-12-12
forum: Desktop Environments
---

### Post by themattjon on 2008-12-12
I got sick of Firefox's constant crashing, stuttering and inability to shut down without restarting Ubuntu, so I installed SeaMonkey and Epiphany to try them out. SeaMonkey's working good, but I can't find Epiphany anywhere under the Applications menu. Shouldn't it show up under Internet?
Where's it at and how do I get it started to check it out?

---

### Post by aysiu on 2008-12-12
Did you install *epiphany* or *epiphany-browser*?

The *epiphany-browser* package is for the Epiphany web browser. *epiphany* is a clone of the BoulderDash Game.

Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
sudo updatedb
locate epiphany
cat /etc/lsb-release
uname -m
dpkg -s epiphany-browser
dpkg -s epiphany
``` The first command may take a few moments to execute. Please be patient.

---

### Post by themattjon on 2008-12-13
HAVE FUN:

/usr/share/doc/epiphany-gecko/changelog.gz
/usr/share/doc/epiphany-gecko/copyright
/usr/share/epiphany-browser/about.ini
/usr/share/epiphany-browser/art
/usr/share/epiphany-browser/chrome
/usr/share/epiphany-browser/components
/usr/share/epiphany-browser/default-prefs.js
/usr/share/epiphany-browser/ephy-xml2ini.xsl
/usr/share/epiphany-browser/epiphany-bookmark-editor-ui.xml
/usr/share/epiphany-browser/epiphany-bookmarks-html.xsl
/usr/share/epiphany-browser/epiphany-bookmarksbar.xml
/usr/share/epiphany-browser/epiphany-fs-toolbar.xml
/usr/share/epiphany-browser/epiphany-history-window-ui.xml
/usr/share/epiphany-browser/epiphany-toolbar.xml
/usr/share/epiphany-browser/epiphany-ui.xml
/usr/share/epiphany-browser/epiphany.xhtml
/usr/share/epiphany-browser/glade
/usr/share/epiphany-browser/icons
/usr/share/epiphany-browser/mime-types-permissions.xml
/usr/share/epiphany-browser/chrome/app-chrome.manifest
/usr/share/epiphany-browser/chrome/branding
/usr/share/epiphany-browser/chrome/global
/usr/share/epiphany-browser/chrome/branding/brand.dtd
/usr/share/epiphany-browser/chrome/branding/brand.properties
/usr/share/epiphany-browser/chrome/global/about.xhtml
/usr/share/epiphany-browser/chrome/global/netError.dtd
/usr/share/epiphany-browser/components/epiphany.xpt
/usr/share/epiphany-browser/glade/certificate-dialogs.glade
/usr/share/epiphany-browser/glade/epiphany.glade
/usr/share/epiphany-browser/glade/form-signing-dialog.glade
/usr/share/epiphany-browser/glade/prefs-dialog.glade
/usr/share/epiphany-browser/glade/print.glade
/usr/share/epiphany-browser/icons/hicolor
/usr/share/epiphany-browser/icons/hicolor/16x16
/usr/share/epiphany-browser/icons/hicolor/22x22
/usr/share/epiphany-browser/icons/hicolor/24x24
/usr/share/epiphany-browser/icons/hicolor/32x32
/usr/share/epiphany-browser/icons/hicolor/48x48
/usr/share/epiphany-browser/icons/hicolor/scalable
/usr/share/epiphany-browser/icons/hicolor/16x16/actions
/usr/share/epiphany-browser/icons/hicolor/16x16/places
/usr/share/epiphany-browser/icons/hicolor/16x16/status
/usr/share/epiphany-browser/icons/hicolor/16x16/actions/bookmark-view.png
/usr/share/epiphany-browser/icons/hicolor/16x16/actions/history-view.png
/usr/share/epiphany-browser/icons/hicolor/16x16/actions/location-entry.png
/usr/share/epiphany-browser/icons/hicolor/16x16/places/bookmark-web.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/ad-blocked.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/feed-presence.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/lock-broken.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/lock-insecure.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/lock-secure-checked.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/lock-secure.png
/usr/share/epiphany-browser/icons/hicolor/16x16/status/popup-hidden.png
/usr/share/epiphany-browser/icons/hicolor/22x22/actions
/usr/share/epiphany-browser/icons/hicolor/22x22/places
/usr/share/epiphany-browser/icons/hicolor/22x22/status
/usr/share/epiphany-browser/icons/hicolor/22x22/actions/bookmark-view.png
/usr/share/epiphany-browser/icons/hicolor/22x22/actions/history-view.png
/usr/share/epiphany-browser/icons/hicolor/22x22/actions/location-entry.png
/usr/share/epiphany-browser/icons/hicolor/22x22/places/bookmark-web.png
/usr/share/epiphany-browser/icons/hicolor/22x22/status/ad-blocked.png
/usr/share/epiphany-browser/icons/hicolor/22x22/status/feed-presence.png
/usr/share/epiphany-browser/icons/hicolor/22x22/status/popup-hidden.png
/usr/share/epiphany-browser/icons/hicolor/24x24/actions
/usr/share/epiphany-browser/icons/hicolor/24x24/places
/usr/share/epiphany-browser/icons/hicolor/24x24/status
/usr/share/epiphany-browser/icons/hicolor/24x24/actions/bookmark-view.png
/usr/share/epiphany-browser/icons/hicolor/24x24/actions/history-view.png
/usr/share/epiphany-browser/icons/hicolor/24x24/actions/location-entry.png
/usr/share/epiphany-browser/icons/hicolor/24x24/places/bookmark-web.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/ad-blocked.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/feed-presence.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/lock-broken.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/lock-insecure.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/lock-secure-checked.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/lock-secure.png
/usr/share/epiphany-browser/icons/hicolor/24x24/status/popup-hidden.png
/usr/share/epiphany-browser/icons/hicolor/32x32/actions
/usr/share/epiphany-browser/icons/hicolor/32x32/status
/usr/share/epiphany-browser/icons/hicolor/32x32/actions/bookmark-view.png
/usr/share/epiphany-browser/icons/hicolor/32x32/actions/history-view.png
/usr/share/epiphany-browser/icons/hicolor/32x32/actions/location-entry.png
/usr/share/epiphany-browser/icons/hicolor/32x32/actions/location-entry.svg
/usr/share/epiphany-browser/icons/hicolor/32x32/status/feed-presence.png
/usr/share/epiphany-browser/icons/hicolor/32x32/status/popup-hidden.png
/usr/share/epiphany-browser/icons/hicolor/48x48/status
/usr/share/epiphany-browser/icons/hicolor/48x48/status/lock-broken.png
/usr/share/epiphany-browser/icons/hicolor/48x48/status/lock-insecure.png
/usr/share/epiphany-browser/icons/hicolor/48x48/status/lock-secure-checked.png
/usr/share/epiphany-browser/icons/hicolor/48x48/status/lock-secure.png
/usr/share/epiphany-browser/icons/hicolor/scalable/actions
/usr/share/epiphany-browser/icons/hicolor/scalable/status
/usr/share/epiphany-browser/icons/hicolor/scalable/actions/bookmark-view.svg
/usr/share/epiphany-browser/icons/hicolor/scalable/actions/history-view.svg
/usr/share/epiphany-browser/icons/hicolor/scalable/actions/location-entry.svg
/usr/share/epiphany-browser/icons/hicolor/scalable/status/feed-presence.svg
/usr/share/epiphany-browser/icons/hicolor/scalable/status/popup-hidden.svg
/usr/share/epiphany-extensions/adblock-patterns
/usr/share/epiphany-extensions/ephy-gestures.xml
/usr/share/epiphany-extensions/glade
/usr/share/epiphany-extensions/xml
/usr/share/epiphany-extensions/glade/action-properties.glade
/usr/share/epiphany-extensions/glade/actions-editor.glade
/usr/share/epiphany-extensions/glade/adblock.glade
/usr/share/epiphany-extensions/glade/epilicious-config.glade
/usr/share/epiphany-extensions/glade/epilicious-progress.glade
/usr/share/epiphany-extensions/glade/error-viewer.glade
/usr/share/epiphany-extensions/glade/extensions-manager-ui.glade
/usr/share/epiphany-extensions/glade/livehttpheaders-ui.glade
/usr/share/epiphany-extensions/glade/page-info.glade
/usr/share/epiphany-extensions/glade/rss-ui.glade
/usr/share/epiphany-extensions/xml/epiphany-sidebar-ui.xml
/usr/share/epiphany-extensions/xml/page-info-context-ui.xml
/usr/share/gconf/defaults/10_epiphany-browser-data
/usr/share/gconf/schemas/epiphany-fonts.schemas
/usr/share/gconf/schemas/epiphany-lockdown.schemas
/usr/share/gconf/schemas/epiphany-pango.schemas
/usr/share/gconf/schemas/epiphany.schemas
/usr/share/gnome/help/epiphany-browser
/usr/share/gnome/help/epiphany-extensions
/usr/share/gnome/help/epiphany-browser/C
/usr/share/gnome/help/epiphany-browser/bg
/usr/share/gnome/help/epiphany-browser/ca
/usr/share/gnome/help/epiphany-browser/cs
/usr/share/gnome/help/epiphany-browser/de
/usr/share/gnome/help/epiphany-browser/el
/usr/share/gnome/help/epiphany-browser/en_GB
/usr/share/gnome/help/epiphany-browser/es
/usr/share/gnome/help/epiphany-browser/eu
/usr/share/gnome/help/epiphany-browser/fi
/usr/share/gnome/help/epiphany-browser/fr
/usr/share/gnome/help/epiphany-browser/it
/usr/share/gnome/help/epiphany-browser/ja
/usr/share/gnome/help/epiphany-browser/nl
/usr/share/gnome/help/epiphany-browser/oc
/usr/share/gnome/help/epiphany-browser/ru
/usr/share/gnome/help/epiphany-browser/sv
/usr/share/gnome/help/epiphany-browser/uk
/usr/share/gnome/help/epiphany-browser/C/epiphany.xml
/usr/share/gnome/help/epiphany-browser/C/figures
/usr/share/gnome/help/epiphany-browser/C/legal.xml
/usr/share/gnome/help/epiphany-browser/C/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/C/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/C/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/C/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/bg/epiphany.xml
/usr/share/gnome/help/epiphany-browser/bg/figures
/usr/share/gnome/help/epiphany-browser/bg/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/bg/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/bg/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/bg/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/ca/epiphany.xml
/usr/share/gnome/help/epiphany-browser/ca/figures
/usr/share/gnome/help/epiphany-browser/ca/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/ca/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/ca/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/ca/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/cs/epiphany.xml
/usr/share/gnome/help/epiphany-browser/cs/figures
/usr/share/gnome/help/epiphany-browser/cs/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/cs/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/cs/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/cs/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/de/epiphany.xml
/usr/share/gnome/help/epiphany-browser/de/figures
/usr/share/gnome/help/epiphany-browser/de/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/de/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/de/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/de/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/el/epiphany.xml
/usr/share/gnome/help/epiphany-browser/el/figures
/usr/share/gnome/help/epiphany-browser/el/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/el/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/el/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/el/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/en_GB/epiphany.xml
/usr/share/gnome/help/epiphany-browser/en_GB/figures
/usr/share/gnome/help/epiphany-browser/en_GB/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/en_GB/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/en_GB/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/en_GB/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/es/epiphany.xml
/usr/share/gnome/help/epiphany-browser/es/figures
/usr/share/gnome/help/epiphany-browser/es/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/es/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/es/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/es/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/eu/epiphany.xml
/usr/share/gnome/help/epiphany-browser/eu/figures
/usr/share/gnome/help/epiphany-browser/eu/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/eu/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/eu/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/eu/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/fi/epiphany.xml
/usr/share/gnome/help/epiphany-browser/fi/figures
/usr/share/gnome/help/epiphany-browser/fi/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/fi/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/fi/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/fi/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/fr/epiphany.xml
/usr/share/gnome/help/epiphany-browser/fr/figures
/usr/share/gnome/help/epiphany-browser/fr/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/fr/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/fr/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/fr/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/it/epiphany.xml
/usr/share/gnome/help/epiphany-browser/it/figures
/usr/share/gnome/help/epiphany-browser/it/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/it/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/it/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/it/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/ja/epiphany.xml
/usr/share/gnome/help/epiphany-browser/ja/figures
/usr/share/gnome/help/epiphany-browser/ja/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/ja/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/ja/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/ja/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/nl/epiphany.xml
/usr/share/gnome/help/epiphany-browser/nl/figures
/usr/share/gnome/help/epiphany-browser/nl/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/nl/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/nl/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/nl/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/oc/epiphany.xml
/usr/share/gnome/help/epiphany-browser/oc/figures
/usr/share/gnome/help/epiphany-browser/oc/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/oc/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/oc/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/oc/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/ru/epiphany.xml
/usr/share/gnome/help/epiphany-browser/ru/figures
/usr/share/gnome/help/epiphany-browser/ru/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/ru/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/ru/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/ru/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/sv/epiphany.xml
/usr/share/gnome/help/epiphany-browser/sv/figures
/usr/share/gnome/help/epiphany-browser/sv/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/sv/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/sv/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/sv/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-browser/uk/epiphany.xml
/usr/share/gnome/help/epiphany-browser/uk/figures
/usr/share/gnome/help/epiphany-browser/uk/figures/ephy-addressbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/uk/figures/ephy-bookmarkbar-smartbookmark-screenshot.png
/usr/share/gnome/help/epiphany-browser/uk/figures/ephy-history-window-screenshot.png
/usr/share/gnome/help/epiphany-browser/uk/figures/ephy-screenshot.png
/usr/share/gnome/help/epiphany-extensions/C
/usr/share/gnome/help/epiphany-extensions/es
/usr/share/gnome/help/epiphany-extensions/oc
/usr/share/gnome/help/epiphany-extensions/sv
/usr/share/gnome/help/epiphany-extensions/C/epiphany-extensions.xml
/usr/share/gnome/help/epiphany-extensions/C/figures
/usr/share/gnome/help/epiphany-extensions/C/legal.xml
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-action-create.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-adblocker.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-back.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-close-2.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-close.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-forward.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-fullscreen.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-homepage.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-new-tab.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-new-window.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-next-tab.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-prev-tab.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-reload.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-stop.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-up.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-view-source-2.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-gestures-view-source.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-sidebar.png
/usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-tabgroups.png
/usr/share/gnome/help/epiphany-extensions/es/epiphany-extensions.xml
/usr/share/gnome/help/epiphany-extensions/es/figures
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-action-create.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-adblocker.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-back.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-close-2.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-close.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-forward.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-fullscreen.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-homepage.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-new-tab.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-new-window.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-next-tab.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-prev-tab.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-reload.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-stop.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-up.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-view-source-2.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-gestures-view-source.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-sidebar.png
/usr/share/gnome/help/epiphany-extensions/es/figures/epi-ext-tabgroups.png
/usr/share/gnome/help/epiphany-extensions/oc/epiphany-extensions.xml
/usr/share/gnome/help/epiphany-extensions/oc/figures
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-action-create.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-adblocker.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-back.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-close-2.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-close.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-forward.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-fullscreen.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-homepage.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-new-tab.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-new-window.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-next-tab.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-prev-tab.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-reload.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-stop.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-up.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-view-source-2.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-gestures-view-source.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-sidebar.png
/usr/share/gnome/help/epiphany-extensions/oc/figures/epi-ext-tabgroups.png
/usr/share/gnome/help/epiphany-extensions/sv/epiphany-extensions.xml
/usr/share/gnome/help/epiphany-extensions/sv/figures
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-action-create.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-adblocker.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-back.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-close-2.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-close.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-forward.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-fullscreen.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-homepage.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-new-tab.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-new-window.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-next-tab.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-prev-tab.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-reload.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-stop.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-up.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-view-source-2.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-gestures-view-source.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-sidebar.png
/usr/share/gnome/help/epiphany-extensions/sv/figures/epi-ext-tabgroups.png
/usr/share/icons/hicolor/48x48/apps/epiphany-bookmarks.png
/usr/share/locale-langpack/en_AU/LC_MESSAGES/epiphany.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/epiphany-extensions-2.22.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/epiphany.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/epiphany-extensions-2.22.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/epiphany.mo
/usr/share/man/man1/epiphany-browser.1.gz
/usr/share/man/man1/epiphany.1.gz
/usr/share/menu/epiphany-gecko
/usr/share/omf/epiphany-browser
/usr/share/omf/epiphany-extensions
/usr/share/omf/epiphany-browser/epiphany-C.omf
/usr/share/omf/epiphany-browser/epiphany-bg.omf
/usr/share/omf/epiphany-browser/epiphany-ca.omf
/usr/share/omf/epiphany-browser/epiphany-cs.omf
/usr/share/omf/epiphany-browser/epiphany-de.omf
/usr/share/omf/epiphany-browser/epiphany-el.omf
/usr/share/omf/epiphany-browser/epiphany-en_GB.omf
/usr/share/omf/epiphany-browser/epiphany-es.omf
/usr/share/omf/epiphany-browser/epiphany-eu.omf
/usr/share/omf/epiphany-browser/epiphany-fi.omf
/usr/share/omf/epiphany-browser/epiphany-fr.omf
/usr/share/omf/epiphany-browser/epiphany-it.omf
/usr/share/omf/epiphany-browser/epiphany-ja.omf
/usr/share/omf/epiphany-browser/epiphany-nl.omf
/usr/share/omf/epiphany-browser/epiphany-oc.omf
/usr/share/omf/epiphany-browser/epiphany-ru.omf
/usr/share/omf/epiphany-browser/epiphany-sv.omf
/usr/share/omf/epiphany-browser/epiphany-uk.omf
/usr/share/omf/epiphany-extensions/epiphany-extensions-C.omf
/usr/share/omf/epiphany-extensions/epiphany-extensions-es.omf
/usr/share/omf/epiphany-extensions/epiphany-extensions-oc.omf
/usr/share/omf/epiphany-extensions/epiphany-extensions-sv.omf
/var/cache/apt/archives/epiphany-browser-data_2.24.1-0ubuntu1_all.deb
/var/cache/apt/archives/epiphany-browser_2.24.1-0ubuntu1_all.deb
/var/cache/apt/archives/epiphany-extensions_2.24.1-0ubuntu1_amd64.deb
/var/cache/apt/archives/epiphany-gecko_2.24.1-0ubuntu1_amd64.deb
/var/lib/dpkg/alternatives/epiphany-browser
/var/lib/dpkg/info/epiphany-browser-data.conffiles
/var/lib/dpkg/info/epiphany-browser-data.list
/var/lib/dpkg/info/epiphany-browser-data.md5sums
/var/lib/dpkg/info/epiphany-browser-data.postinst
/var/lib/dpkg/info/epiphany-browser-data.postrm
/var/lib/dpkg/info/epiphany-browser-data.prerm
/var/lib/dpkg/info/epiphany-browser.list
/var/lib/dpkg/info/epiphany-browser.md5sums
/var/lib/dpkg/info/epiphany-extensions.list
/var/lib/dpkg/info/epiphany-extensions.md5sums
/var/lib/dpkg/info/epiphany-extensions.postinst
/var/lib/dpkg/info/epiphany-extensions.postrm
/var/lib/dpkg/info/epiphany-extensions.prerm
/var/lib/dpkg/info/epiphany-gecko.list
/var/lib/dpkg/info/epiphany-gecko.md5sums
/var/lib/dpkg/info/epiphany-gecko.postinst
/var/lib/dpkg/info/epiphany-gecko.postrm
/var/lib/dpkg/info/epiphany-gecko.prerm
matthew@matthew-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
matthew@matthew-desktop:~$ uname -m
x86_64
matthew@matthew-desktop:~$ dpkg -s epiphany-browser
Package: epiphany-browser
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 76
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: all
Version: 2.24.1-0ubuntu1
Depends: epiphany-gecko | epiphany-webkit
Description: Intuitive web browser - dummy package
 Epiphany is a simple yet powerful GNOME web browser targeted at
 non-technical users. Its principles are simplicity and standards
 compliance.
 .
 This dummy package installs Epiphany with the Gecko backend by default.
Original-Maintainer: Josselin Mouette <joss@debian.org>
matthew@matthew-desktop:~$ dpkg -s epiphany
Package `epiphany' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by themattjon on 2008-12-13
Found it! I guess I didn't have every file I needed downloaded...

---

