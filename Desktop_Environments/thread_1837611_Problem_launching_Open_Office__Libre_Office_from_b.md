---
title: "Problem launching Open Office / Libre Office from browser with webdav document -11.04"
date: 2011-09-02
forum: Desktop Environments
---

### Post by DPJB on 2011-09-02
Hi,

I have a website with links to webdav shared documents like this:

vnd.sun.star.webdav://some.url.here/webdav/export/2011.06.0009.odt

I used gconf to add the url handler for vnd.sun.star.webdav:

gconftool-2 --set --type=string /desktop/gnome/url-handlers/vnd.sun.star.webdav/command 'soffice "%s"'
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/vnd.sun.star.webdav/enabled true
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/vnd.sun.star.webdav/need-terminal false

In 10.04 this used to work flawless. Upon clicking the link in chromium, Open Office would launch and I could happily edit. In 11.04, this no longer works and I have no idea why not... 11.04 has Libre Office, but the executable is still /usr/bin/soffice, so this shouldn't matter too much.

Help appreciated!

Thanks,

Dirk

---

