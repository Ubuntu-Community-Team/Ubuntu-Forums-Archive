---
title: "sudo is pestering me"
date: 2009-01-04
forum: General Help
---

### Post by jtgd on 2009-01-04
I just upgraded from Feisty to Intrepid.  It used to be that sudo would only prompt for my password once every login session, then it would remember forever.  Now it only remembers for like 5 minutes.  I would like it to be like before and not constantly prompt me.  Did they change something between versions?  

I have added myself to admin and sudo groups, and have fiddled with /etc/sudoers and added the lines:

[INDENT]   myusername ALL = (ALL) ALL[/INDENT]

and/or:

[INDENT]   myusername ALL = NOPASSWD: ALL[/INDENT]

but that seems to have no effect.  Do I need to reboot for that?

(If it matters, I have installed KDE3 after the normal Kubuntu amd64 install)

---

### Post by Sef on 2009-01-04
How did you upgrade from Feisty to Intrepid?

---

### Post by jtgd on 2009-01-04
> **Sef said:**
> How did you upgrade from Feisty to Intrepid?
I installed from CD: kubuntu-8.10-desktop-amd64.iso five days ago.
I got fed up with KDE4 so installed Gnome briefly, then installed KDE 3.5.10.

I did save my old /etc and /boot directories from Feisty so I can refer to them.  The old /etc/sudoers didn't seem to have anything special in it and I don't believe I ever edited it.

---

### Post by caljohnsmith on 2009-01-04
Did you make sure to put:
```
<myusername> ALL = NOPASSWD: ALL
```
At the very end of the sudoers file? In other words, the order of the rules in /etc/sudoers matters, and you should put the above line after the line that has:
```
%admin ALL=(ALL) ALL
```
Assuming you are part of the admin group, because if you don't, then the above rule overrides your nopasswd rule. So if you put that first line above at the very end of the sudoers file, you should be fine. Let me know how it goes.

---

### Post by jtgd on 2009-01-05
> **caljohnsmith said:**
> Did you make sure to put:
```
<myusername> ALL = NOPASSWD: ALL
```
At the very end of the sudoers file? In other words, the order of the rules in /etc/sudoers matters, and you should put the above line after the line that has:
```
%admin ALL=(ALL) ALL
```
Assuming you are part of the admin group, because if you don't, then the above rule overrides your nopasswd rule. So if you put that first line above at the very end of the sudoers file, you should be fine. Let me know how it goes.

That was it!  Thanks much!

---

### Post by jtgd on 2009-01-05
(adding SOLVED)

---

