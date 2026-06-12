---
title: "Random applications Turning on when the computer is locked"
date: 2020-12-27
forum: Desktop Environments
---

### Post by lestnitsa on 2020-12-27
Hi,

I use 20.04 LTS with Gnome. My computer is set to stay turned on when the lid is closed, the problem is that, when I close the lid, screen is locked, and when I get back to my computer and enter the password and access the desktop again, there are often random applications turned on and sometimes 5-10 instances/windows of the same application, or, if my memory doesn't fail me, new tabs opened on my browser or some things have gotten clicked on in the applications opened, so they are not always in the untouched freshly opened window state. I've had this problem since 18.04 and idk why it didn't bother me until now. But I'm afraid one day it will end up sending a message or removing a file that shouldn't etc etc.

I think this might be because my computer generates random keystrokes or touchpad-strokes when the lid is closed and the desktop is locked, however I should note that this happens even if don't touch the computer at all, and 20-30 windows opened randomly is beyond what could I do just touching random buttons while the lid is closed, and it's not like I can do anything in the desktop while the computer locked, in the end it's locked and I can't do anything on the desktop, but the computer does things by itself, which is annoying because I have to close many windows almost every time I login back.

Has any one had this before? What are your suggestions? I want to defenstrate this computer.

Thank you for reading,
Faruk

---

### Post by TheFu on 2020-12-27
replace the keyboard?

---

### Post by lestnitsa on 2020-12-29
As I noted, it's not to do with the keyboard. It happens when the desktop is locked a.k.a when the keyboard has no access to the desktop. Computer runs scripts or maybe keyboard shortcuts by itself when locked.

---

### Post by QIII on 2020-12-29
Where is your computer?  Is it on a wired or wireless connection?  Is it on a network in common with other machines?  Does anyone else have physical access to the machine?  Do you allow remote access via ssh or similar?  Is that by password or key pair?

Did you upgrade to 20.04 or did you do a fresh installation?

---

### Post by dino99 on 2020-12-30
Goto the 'journalctl -b' output to know what is going on when the lid is closed as you said.
maybe do some ghost hunting too.

---

