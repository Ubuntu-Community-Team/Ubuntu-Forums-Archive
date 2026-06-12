---
title: "UEFI boot issues"
date: 2015-10-03
forum: Debian
---

### Post by ferreret2 on 2015-10-03
Hello,

My problem si that GNU GRUB doesn't appear when I boot my computer. I did what this link explains ([http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)). It doesn't appear any message of error, so I think it's fine, but when I reboot the pc the problem persists. I've tried with boot-repair, but it gives me an error and the software tells me I have to write a message to administrators of boot-repair. The Info Summary of my pc, given by boot-repair is this (paste.ubuntu.com/12648217).

Can anyone help me, please?

Thanks.

---

### Post by oldfred on 2015-10-03
Moved to your own thread, since old thread was solved and few will review it.

Also moved to Debian sub-formum. It looks like you did have Ubuntu installed, but now have Debian.

Your link, that can be just clicked on:
[http://ubuntuforums.org/showthread.php?t=2297406](http://ubuntuforums.org/showthread.php?t=2297406)
Install looks typical UEFI only, but some brands have issues that we have to work around. 
Not sure what is different with Debian, as Ubuntu adds, updates some things, but is based on Debian.

What brand/model computer.
When you reboot you will not get a grub install error, what error do you get?

---

### Post by ferreret2 on 2015-10-03
Thanks for moving it to my own threat! 

Effectively, first of all I had windows. Then I installed ubuntu 14.04 with no errors. But when I installed debian appeared this error. My PC is an HP 650 Core i3. When I reboot the system there's no error. I see this image ([http://i.stack.imgur.com/BLbvW.jpg](http://i.stack.imgur.com/BLbvW.jpg)) but my version is GNU GRUB version 2.02-beta2-9ubuntu1.3.

Thanks for your help.

---

### Post by ferreret2 on 2015-10-03
Now I've tried with Super Grub2 Disk and I've achieved to enter in debian. Then I opened a terminal and writed
```
sudo grub-install --recheck /dev/sda
```
and
```
sudo grub-install --recheck /dev/sda
```

But when I reboot, the problem persists. I see the same image I told in the last post. It never ends :/

---

### Post by The_Forgotten_King on 2015-10-03
> **ferreret2 said:**
> Now I've tried with Super Grub2 Disk and I've achieved to enter in debian. Then I opened a terminal and writed
```
sudo grub-install --recheck /dev/sda
```
and
```
sudo grub-install --recheck /dev/sda
```

But when I reboot, the problem persists. I see the same image I told in the last post. It never ends :/
The two codes are the same? Did you enter them twice? Or am I missing something. Had them same problem, but it went away after a while, no idea why.

---

### Post by ferreret2 on 2015-10-03
Sorry, I copied the same. The second code I wanted to paste was:
```
sudo update-grub
```

---

### Post by ferreret2 on 2015-10-04
Do you think that my problem is the  'Problem2:EFI boot entries disappear after reboot'? If it is the case, I don't understand the solution they talk about.

LINK: [https://wiki.debian.org/GrubEFIReinstall](https://wiki.debian.org/GrubEFIReinstall)

---

### Post by ferreret2 on 2015-10-04
I've done what that link says but the problem is still persisting... I don't have any idea. Do you think if I install again Ubuntu the problem will be resolved?

EDIT: Problem "solved". I've turned back to Ubuntu and now it boots correctly. I wanted to know the solution to my problem but I couldn't wait more time.

---

