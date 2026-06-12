---
title: "libcanberra problem or maybe xdilog"
date: 2009-05-31
forum: General Help
---

### Post by Lostin60's on 2009-05-31
Where to start? Well here is my command and error msg.
> daniel@mypos:~$ xbindkeys-config

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Segmentation fault

However the file is there.  It seems this exact msg runs amok in many different apps. Google has tons of entries about this msg, and each one seem to deal with a different app. I think there is a workaround here,

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/368175]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/368175")

but it doesn't spell things out enough for me to try the workaround. I understand the problem, I understand the rationale behind the workaround. But if I understand correctly that the workaround is to be applied to the xdialog file, it is binary, and I can't gedit it.

The thing is, the libcanberra-gtk-module.so file only deals with audio, and has no reason to be called at all for anything else.

If someone looks at the posts in the above link, they will get a better idea of the issue.  And if anyone can translate the...umm (geekspeak?) into English for me I think I can handle doing the workaround. As always, any and all help will be greatly appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by livigagl on 2009-07-30
I have the same problem using oald7 (Oxford Advanced Learner's Dictionary).
The lib libcanberra-gtk-module.so is present in /usr/lib/gtk-2.0/modules/, if I create a link to it in /usr/lib/ I doesn't receive the Gtk-WARNING but instead of it I receive:
```
/home/myname/oald/application/run-oald7.sh: line 159: 32068 Segmentation fault      "$prog" ${1+"$@"}
```
just to check if I have the problem with other applications I installed xbindkeys-config (and its dependencies) and it runs but oald7 still doesn't.
I'm using Debian Lenny in two computers, same configuration (same repositories), in one of them it works and in the other it doesn't.
I'm going crazy. Please if someone knows something to give me at least a clue I really appreciate. :-)

---

### Post by livigagl on 2009-07-30
I've forgotten to say that if i run the program as root (with sudo) it works.
And... on the other pc where it works as a normal user I receive the warning in the terminal but it starts and works perfectly.

---

### Post by slymi2005 on 2009-07-30
I get this error when I run firefox from the terminal:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

---

### Post by livigagl on 2009-07-30
weird... I don't have any issue with firefox or with other applications (as far as I know) except oald7.

---

