---
title: "Xbox series X|S controller won't connect via USB (or Bluetooth) on Ubuntu 23.10"
date: 2023-11-26
forum: Gaming &amp; Leisure
---

### Post by brav3ry on 2023-11-26
I used to be able to connect my controller after I setup ubuntu-xboxdrv. Now it no longer works. It seems like there isn't a version of xboxdrv for Ubuntu 23.10? I don't know if this is the right place to ask this question.

---

### Post by brav3ry on 2023-11-29
I actually have no idea what to do. I've run lsusb. I've tried purging xboxdrv and ubuntu-xboxdrv. I've tried reinstalling them. Can anyone suggest something I should try next?

---

### Post by DuckHook on 2023-11-29
Why do you have to run 23.10? Most users (including yours truly) stick with LTS releases for the added stability and to avoid precisely the problems that you are running into.

If the previous LTS configuration worked for you (assuming that this was Jammy 22.04), then I recommend sticking with that. It still has 3+ years of support left. Allow others to do the experimenting and bug hunting. Of course, if you wish to contribute to ongoing development, then dual booting into the latest standard version for testing/bug-hunting is appreciated, but it shouldn't be your working platform.

---

### Post by brav3ry on 2023-11-30
You're right, I should have. That being said I don't know how to restore my 22.04 backup (and even if i could, there would be stuff lost between then and now). And 23.10 still works well enough, even a the worst, I could perhaps wait for the next LTS? Would that be 24.04? Not being able to use my controller is quite frustrating, but not exactly necessary. I'd still like to make it work though.

---

### Post by DuckHook on 2023-12-01
You could try dual booting, although preparing your rig to install Jammy requires a bit of care not to wipe out your existing install. Still, lots of people do this. I triple boot with two LTS partitions and the latest standard version on the third partition. If you back up your current data (and test that backup) so that a reinstall becomes only an inconvenience, then there should be no barrier to making a dual boot.

I can't help you unravel your xbox controller issue on 23.10 because I have no such gear. Perhaps others who share your HW have encountered this and can chime in.

I would also caution you against expecting this problem to be solved in 24.04. Though it will be a LTS, it isn't magical. It seems that the older releases worked because they were well synchronized with your driver. The new releases seem to have broken that synchronicity and this is unlikely to be solved just because the next release is LTS—not right away at any rate. The nature of Linux is one of constant updates and a future update could very well solve your problem, but no one can predict if/when that will happen.

Aside from advising a return to 22.04 (whether as a dual boot or an outright reinstall), I'm out of options. Sorry.

---

### Post by julian552 on 2023-12-09
Hi, did you manage to fix it?

[RIGHT][SIZE=1][URL="https://www.minimilitia.mobi/"][COLOR=#a9a9a9]

Mini Militia[/COLOR][/URL] [[COLOR=#a9a9a9]App Lock[/COLOR]]("https://www.applock.ooo/")[/SIZE][/RIGHT]

---

### Post by brav3ry on 2023-12-09
No.

---

