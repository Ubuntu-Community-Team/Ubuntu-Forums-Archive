---
title: "getting Picasa working just right"
date: 2007-10-21
forum: Desktop Environments
---

### Post by rogerdean on 2007-10-21
hello folks

i'm trying to tweak picasa so that it integrates properly with my desktop (really this sort of thing should just work, i reckon, but i don't mind asking for help either)

i've found some info here and there, and have copied the four template files...
/opt/picasa/desktop/picasa-hook-email.sh.template
/opt/picasa/desktop/picasa-hook-urlhandler.sh.template
/opt/picasa/desktop/picasa-hook-mimehandler.sh.template
/opt/picasa/desktop/picasa-hook-filemanager.sh.template

to...
/opt/picasa/bin/picasa-hook-email.sh
/opt/picasa/bin/picasa-hook-urlhandler.sh
/opt/picasa/bin/picasa-hook-mimehandler.sh
/opt/picasa/bin/picasa-hook-filemanager.sh

now, the [Picasa Community Ubuntu Documentation]("https://help.ubuntu.com/community/Picasa") page tells me that I need to put the line...
/usr/bin/nautilus "${1%%$(basename "$1")}"
...into the picasa-hook-filemanager.sh file, and this works fine. I can now use the 'Export' button at the bottom of the Picasa window.

What I really still need is to get the email hook working - what should the command be here (I use thunderbird)? I guess it'd also be good to get the other commands too (although i don't even know what the mimehandler hook would be for!). Can anyone help me out with this please?

Many thanks to all
Roger

---

### Post by rogerdean on 2007-10-28
ok, for now i've settled for emailing photos with picasa's gmail conduit, so that'll have to do. surely someone knows how this is supposed to work though??
R

---

