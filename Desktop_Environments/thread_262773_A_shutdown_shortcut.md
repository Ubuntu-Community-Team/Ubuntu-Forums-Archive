---
title: "A shutdown shortcut?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Guillaumeb on 2006-09-22
Hi all,

ever since i installed AIGLX + Compiz over Ubuntu, the shutdown button freezes my computer.

Also Compiz does not automatically start. 

I created a compiz-start shortcut to launch it.

Now i wouild like to create a shortcut to shut down/restart my computer instead of opening the terminal and typing:

sudo -s
paswword
halt or reboot

Since we need to be at the root i don't know how to make this shortcut.

anyone can help me here?

thank you

---

### Post by ayoli on 2006-09-22
that's a known bug, here is a solution:
create a .gnomerc file in your homedir and put this in:
```
export GSM_NO_GRAB_SERVER=1
```
then logout (ctrl+alt+backspace) and login again, should work.*

note: this fix works only for dapper since compiz repos for dapper provides a patched gnome-session package.

---

### Post by shinkaide on 2006-09-22
Hi, I'd like to know if this will work in fluxbox. Do I just create and [exec] menu link to the file and it'll shutdown just like gnome does with the shutdown button? Or is there something else I have to do?

---

### Post by sunny_nwho on 2006-10-11
awesome this works even for a beryl install...thank u mate

---

