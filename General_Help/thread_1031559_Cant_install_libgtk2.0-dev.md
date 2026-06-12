---
title: "Cant install libgtk2.0-dev??"
date: 2009-01-05
forum: General Help
---

### Post by Psyphre on 2009-01-05
Hi,

Ive been trying to install some gtk theme engines (specifically aurora and murrine svn), however when i try to compile it comes up with an error regarding no gtk2.0. So i tried to install libgtk2.0-dev but I get this error:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-3ubuntu5) but 2.12.9-4ubuntu3 is to be installed

and just wont install it. I have no idea why its doing this and how to resolve it.
Does anyone know why?

Thanks in advance.

Psyphre.

---

### Post by mc4man on 2009-01-05
To start go into System -> admin... -> software sources and see if under the 'updates' tab if 'Recommended Updates (hardy-updates) is checked. If not checked, then enable and reload.

---

### Post by happyhamster on 2009-01-05
libgtk2.0-0 version 2.12.9-4ubuntu3 doesn't seem to be an official ubuntu package AFAICT.

Hardy started with 2.12.9-3ubuntu2 ([http://packages.ubuntu.com/hardy/libgtk2.0-0](http://packages.ubuntu.com/hardy/libgtk2.0-0)) and currently uses 2.12.9-3ubuntu5 ([http://packages.ubuntu.com/hardy-updates/libgtk2.0-0](http://packages.ubuntu.com/hardy-updates/libgtk2.0-0)). The changelog also doesn't show anything about an 4ubuntu3 version ([http://changelogs.ubuntu.com/changelogs/pool/main/g/gtk+2.0/gtk+2.0_2.12.9-3ubuntu5/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gtk+2.0/gtk+2.0_2.12.9-3ubuntu5/changelog))

So, I think the most likely explanation is that there's an error in the makefile ("4ubuntu3" instead of "3ubuntu4"), or the package is a non-ubuntu one (provided by the developers of those themes for example).

---

### Post by Psyphre on 2009-01-05
Thanks for the replies I appreciate it.

mc4man: They are enabled.

happyhamster: I tried these exact same engines on my laptop and it worked perfectly fine. So it cant be the theme engines.

I just had a thought, I have the global menu applet installed (that emulates a mac menu), could this be the culprit?

---

