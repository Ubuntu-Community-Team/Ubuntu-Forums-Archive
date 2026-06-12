---
title: "11,04 - boots to command prompt, not desktop"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Magick93 on 2011-04-30
Hi

I just did the upgrade, but now when I start my computer I just get a comand prompt and not the typical login screen and desktop.

How can I fix this?

Thanks

---

### Post by Magick93 on 2011-04-30
Bump. Anyone? Would really like to be able to log into my computer again.

---

### Post by xdragonforce on 2011-04-30
Could you give us some more info, are you using Wubi, does the command prompt contain any error mesages?

---

### Post by Magick93 on 2011-04-30
The error I get is Mountall:Disconnected from Plymouth.
mount.nfs:failed to resovle to server fileserver:name or service is not known.

However if I boot into the previous version in the GRUB loader I can start ubuntu normally.

---

### Post by xdragonforce on 2011-05-01
Right, i guess you are running ubuntu sever?

---

### Post by xdragonforce on 2011-05-01
Does the terminal say - (initramfs)

---

### Post by Magick93 on 2011-05-01
Hi xdragonforce

Thanks for helping.

No, I dont believe I am running ubuntu server, and No I did not recall seeing that message. I have a little NAS server, and it seems that when booting ubuntu, after the upgrade cannot connect to nas server. But when I boot and choose an earlier version in the GRUB menu, then ubuntu boots to desktop, with conenctions to the server.

---

### Post by xdragonforce on 2011-05-02
Sorry for not responding so soon

If you can boot into an older version from grub, then chances are that the working version of ubuntu ( im guessing 10.10) is fine, whilst your latest version is corrupted. 

Did you upgrade from within ubuntu or from a LiveCD?

---

### Post by morrisjones on 2011-05-02
I had the same problem, upgrade, no desktop, boots to command prompt.

I found an error in one of the message logs in /var/log that indicated that the video driver fglrx was crashing (firegl_SetSuspendResumeState).

I purged fglrx, replaced it with the open-source ATI driver, removed xconf, and was able to log in using Ubuntu Classic (no effects).

I'm on the amd64 architecture, RV710 Radeon HD 4550 VGA hardware.

Mojo

---

### Post by morrisjones on 2011-05-02
This page was very useful on purging fglrx and installing the ATI driver:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Mojo

---

### Post by Magick93 on 2011-05-14
Hi

I believe this is something to do with the nvidia drivers. 

I have tried reinstalling the nvidia drivers but this did not help. Now I have the same problem when I try to boot to an early version on the grub menu - so it has only made the problem worse.

I found this page that describes my problem: [http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)

However when It tried to edit the grub file as they suggested, when I opened it, it was empty. So I guess it was the wrong file?

I am getting very desperate. I am willing to pay someone so that I can use my computer again!

---

