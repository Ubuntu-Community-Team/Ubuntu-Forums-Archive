---
title: "disable Nautilus extension without uninstalling it"
date: 2009-12-20
forum: Desktop Environments
---

### Post by Khaled Khalil on 2009-12-20
is there some way to disable certain Nautilus extension without uninstalling it ?

when i have nautilus-clamscan extension installed Nautilus takes long time to start, and occupy large space in memory (168MB of resident memory instead 37MB when uninstalled).
however, i still need it to be available, even when i am offline.

i looked in .nautilus and in nautilus's directory in gconf, but no mention to extensions!

---

### Post by Khaled Khalil on 2009-12-20
well, i figured out how to work around this, but still wait to know if there is a more elegant way.

from [Nautilus extensions document]("http://live.gnome.org/Nautilus/Development/Extensions") on live.gnome.org i knew that python extensions are saver in "~/.nautilus/python-extensions" or "/usr/lib/nautilus/extensions-2.0/python" , and c ones are only in "/usr/lib/nautilus/extensions-2.0/" .
i found two files in "/usr/lib/nautilus/extensions-2.0/python" , "nautilus-clamscan.py" and "nautilus-clamscan.pyc" . so i created directory "python-extensions/" in "~/.nautilus/" and copied the two files there, uninstalled nautilus-clamscan package, then restarted nautilus, and it loaded the same bloat successfully, then created directory "disable/" in "~/.nautilus/python-extensions" and moved the two files there, and restarted nautilus and it didn't load the bloody extension.

---

