---
title: "Ubuntu bug or nautilus glitch?"
date: 2006-08-04
forum: Desktop Environments
---

### Post by linuxNewb on 2006-08-04
Should I report this as an Ubuntu bug?

When copying and pasting multiple directories in nautilus, some sub-directories are not actually copied over. The copy over fine if I select them individually, but when selecting a single directory that has many levels of sub-directories, many are not copied over.

This happens when copying files from my hda drive to a usb flash drive '/media/USB20FD'

It does not show any errors to indicate that the files where not copied over. This is very annoying. Thanks.

---

### Post by ESPOiG on 2006-08-04
do it via terminal
see what that shows...

cp \etc\loser\ \media\usb2\loser\

if it does have writing permissions or something it will say, then try that with sudo in front

although i have had a similar problem with fc5 it fails to copy certain directories even in root, but this says error

---

### Post by quonsar on 2006-08-04
this has been noted by myself and others.

see this: [http://www.ubuntuforums.org/showthread.php?t=212148]("http://www.ubuntuforums.org/showthread.php?t=212148")

---

