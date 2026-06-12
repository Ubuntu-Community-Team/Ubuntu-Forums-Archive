---
title: "I've broken SUDO..."
date: 2007-04-23
forum: Desktop Environments
---

### Post by jiggling_john on 2007-04-23
i've just managed to break my etc/sudoers file. Whenever I try to sudo anything I now get the message

sudo: /etc/sudoers is mode 0644, should be 0440

I can'd chmod sudoers... any idea how to fix it?

---

### Post by phidia on 2007-04-23
I would boot from the livecd and then you can even replace the entire sudoers directory with the one from the livecd or just repair it from the livecd.

---

### Post by jiggling_john on 2007-04-23
I happen to have just fixed this. For anyone who ever does the same as me

reboot, press escape to get the boot menu, select recovery mode then when the prompt appears do

chmod 0440 /etc/sudoers

job done... Won't be doing that again in a hurry!

---

