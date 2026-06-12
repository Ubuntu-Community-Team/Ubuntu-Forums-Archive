---
title: "Ctrl+Alt+F1 to Ctrl+Alt+F6 not working in ubuntu"
date: 2009-05-20
forum: Desktop Environments
---

### Post by Vellingiri on 2009-05-20
Dear Guys,
   When I switch over ctrl+alt+f1 to ctrl+alt+f6 it doesn't work in ubuntu . I am able to see only black screen and small cursor is blinking on the top left. What could be possible reason? How do i make it work ? Please any one help me .

With Regards,
  S.Vellingiri.

---

### Post by RoboNuggie on 2009-05-21
Ctrl+Alt+F7 will take you back to your desktop.

---

### Post by lukjad on 2009-05-21
That is... odd. Have you installed anything recently?

---

### Post by RoboNuggie on 2009-05-21
Could it be a framebuffer bug as described : [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

Something along the lines of vesafb and nvidia conflict?

---

### Post by roel46 on 2009-05-22
maybe try: left-alt+left-ctrl+f1
maybe look at:
[LIST]
[*]System > Preferences > Keyboard
[*]System > Preferences > Keyboard Shortcuts
[/LIST]
good luck, roel.

---

### Post by trench.me on 2009-05-22
After upgrading to Jaunty on another machine I've lost all my tty sessions - they can't be accessed at all. This on top of complete xorg failure. I spent 8 hours on it last night to no avail. I'm starting a related thread a bit later when I can provide more informative details - new post because these issues could be completely unrelated, but you never know.

---

### Post by irish0red on 2009-05-22
I dont know if this will help but all my combos started working after i reenabled ctrl-alt-backspace.  This site has the how to [http://maketecheasier.com/restore-ctrl-alt-backspace-in-ubuntu-jaunty/2009/05/17](http://maketecheasier.com/restore-ctrl-alt-backspace-in-ubuntu-jaunty/2009/05/17)
hope that helps!

---

### Post by TheHolm on 2009-05-22
> **Vellingiri said:**
> Dear Guys,
   When I switch over ctrl+alt+f1 to ctrl+alt+f6 it doesn't work in ubuntu . I am able to see only black screen and small cursor is blinking on the top left. What could be possible reason? How do i make it work ? Please any one help me .

With Regards,
  S.Vellingiri.

It seems that no getty running on virtual terminals.
Please check do you have ant getty processes running? 

[I]#ps ax
 4644 tty4     Ss+    0:00 /sbin/getty 38400 tty1[/I]

---

### Post by Dewey_Oxberger on 2009-07-09
On a clean install of mythbuntu 9.04 amd64 with an nvidia 7050 based motherboard it works fine.  Ctrl Alt Fx goes to a tty.

Take that hardware and change the motherboard to an nvidia based 8300, do a clean install, and I have this problem.

---

