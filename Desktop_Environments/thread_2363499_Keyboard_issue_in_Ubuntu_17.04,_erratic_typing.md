---
title: "Keyboard issue in Ubuntu 17.04, erratic typing"
date: 2017-06-10
forum: Desktop Environments
---

### Post by supernova22 on 2017-06-10
Keyboard of my HP spectre laptop was working fine in Ubuntu, but since the upgrade to 17.04 the keyboard is a nightmare, erratic typing, randomly jumping and deleting characters as you type, it's not usable. I've made a fresh install of ubuntu 17.04 and problem is the same, also in the live usb 17.04 session it's the same problem, in Unity or Gnome.

Help please, because I can't find provided assistance on similar problem in 17.04... many thanks in advance!

---

### Post by Autodave on 2017-06-11
Some info on your machine and keyboard might help someone come up with a possible cure. Is the keyboard wired or wireless? Have you tried another keyboard? Did you try another USB port for the keyboard?

---

### Post by supernova22 on 2017-06-14
My machine is an HP spectre x360 laptop, the keyboard is the laptop's keyboard, it's not an external keyboard.. Is there any other information I can provide to help out with ideas?

---

### Post by Autodave on 2017-06-14
My first thought would be to go back a couple of releases and install 16.04 which is a long-term release. I have not heard of that problem: it could be just a but in 17.04.

Also, and some will argue with you here, I personally have never had any luck upgrading an existing install. I always have problems ranging anywhere from a few programs needing re-installed to nothing at all working. I prefer to back up everything (which I do on a regular basis anyhow) and do a fresh install.

---

### Post by supernova22 on 2017-06-15
In 16.04 and 16.10 there was no problem, keyboard was working perfectly fine. I've made a fresh install of 17.04 and keyboard problem is the same, I don't think problem comes from the upgrade path. In a live 17.04 session, problem is the same, so I think it has to do with that release. I would prefer to use 17.04 rather than a 16.x release... :)

---

### Post by waggers2 on 2017-07-23
Try sudo apt-get install xserver-xorg-input-all
Reboot

It sounds like you already have this installed.

Try sudo apt-get --purge autoremove xserver-xorg-input-all && sudo apt-get install xserver-xorg-input-all
Reboot

You can use the 'on screen keyboard' to help you get there.

---

### Post by supernova22 on 2017-07-26
Thanks very much waggers2, I just tried this and it seems to have fixed the problem, my laptop keyboard now works fine in 17.04!

---

### Post by QIII on 2017-07-26
Hello!

If the issue is solved to your satisfaction, would you please use the **Thread Tools** button to mark the thread as **Solved** so that others with the same issue might more easily find the solution?

Thanks!

---

