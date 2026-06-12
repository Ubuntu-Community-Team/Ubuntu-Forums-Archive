---
title: "starting many instances of file manager (nautilus) in gnome 2"
date: 2011-09-18
forum: Desktop Environments
---

### Post by masuch on 2011-09-18
Hi,

When I login into gnome version 2 - there appears a lot of tries to open file manager (nautilus).

Desktop is not active (no icons) but panels have always appeared.

I tried to use following advises from:
  [https://bugzilla.redhat.com/show_bug.cgi?id=485375](https://bugzilla.redhat.com/show_bug.cgi?id=485375)
  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=525718](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=525718)


but seems to me nothing works as the following what I tried:


1 try:
I can stop this behaviour by switch off in gconf-editor:
apps/nautilus/preferences/show_desktop to false.

but desktop icons do not appear - which is correct behaviour but I would like to have desktop icons :)


2 try:
I have tried to comment in:
/usr/share/application/nautilus.desktop
line:
X-GNOME-AutoRestart=true


3. try:
add:
AutostartCondition=GNOME /apps/nautilus/preferences/show_desktop
to /usr/share/application/nautilus.desktop


I have run out of ideas.
Could please anybody can help to linux newbie ?
thank you

---

### Post by masuch on 2011-10-01
Partially solved by:
set apps/nautilus/preferences/show_desktop to false

---

