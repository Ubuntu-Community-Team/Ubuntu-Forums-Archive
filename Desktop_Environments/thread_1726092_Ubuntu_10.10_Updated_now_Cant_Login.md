---
title: "Ubuntu 10.10 Updated now Cant Login"
date: 2011-04-10
forum: Desktop Environments
---

### Post by SilvaNights on 2011-04-10
Hi all,

I updated my laptop running Ubuntu 10.10 desktop, and now when I get to the login screen I cant type or move the mouse and there is no users listed (just a grey Ubuntu login box with no username or password fields).

I have had a look around and cant see what this might be.
Some ahve said try ctrl+alt+f1 or ctrl+alt+f7 but it doesnt do anything.

Any help would be great,

Thanks,

---

### Post by Krytarik on 2011-04-10
Try reinstalling GDM:
- boot into "recovery mode"
- choose "root shell prompt with networking"
- reinstall "gdm" (no need to use 'sudo' since you are already root):
```
apt-get install --reinstall gdm
```
- press Ctrl+Alt+Del to reboot

Greetings.

---

### Post by Copper Bezel on 2011-04-10
For clarification, that's at the GRUB2 menu, right? Accessed by holding Shift (formerly Escape) on startup if not otherwise enabled?

Edit: Just asking, because I think it's hidden by default.

---

### Post by Krytarik on 2011-04-11
> **Copper Bezel said:**
> For clarification, that's at the GRUB2 menu, right? Accessed by holding Shift (formerly Escape) on startup if not otherwise enabled?
Yeah, at least Grub (presumably Grub2 in the OP's case since 10.10 is shipped with those), and yeah, if no other OS is installed, one needs to press Shift (Grub2) or Esc (Grub legacy) by default to make the boot menu appear, I tend to don't mind that. ;)

---

### Post by SilvaNights on 2011-04-16
Sorry for late reply, I tried booting into recovery, it just stops at this:
begin running /scripts/init-bottom

Even after a hour its still there.

To be honest if this machine was completely unusable it wouldnt matter as its one of my spare "toys".

My only concern is if it happens to one of main ubuntu machines/usb stick (lol). Or even worse my ubuntu server.

Like I said im not concerned if we kill it lol.
Any ideas?
Thanks,

---

### Post by Krytarik on 2011-04-16
Boot into a LiveCD and check "/var/log/messages" and "/var/log/Xorg.0.log" for related error messages. If you find any, post them, in code-tags please, use the #-button in the editor therefore.

Also, post the content of "/etc/initramfs-tools/conf.d/resume" and the output of:
```
sudo blkid
```
Just a guess.

---

### Post by alex86 on 2011-04-28
I had the same problem. Recovery mode won't help, but if you boot normally, notice that the clock works and you can plug in a USB keyboard to login. Then execute

apt-get -f install

It worked for me!

Except that to get to an actual login screen, you have to tamper with the GRUB. I recall something about display modes, such as noapic... try this
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Good luck!

---

