---
title: "Minecraft Errors"
date: 2014-05-28
forum: Gaming &amp; Leisure
---

### Post by trevor14 on 2014-05-28
Hey folks~
I searched through the forums for a similar problem to mine but haven't found any so I'm hoping one of you can help me with a solution.

I followed [this guide]("http://www.everydaylinuxuser.com/2014/03/how-to-install-ubuntu-and-minecraft-on.html") on installing Ubuntu onto my HP Chromebook 11 specifically to play Minecraft, and installed Ubuntu 12.04.4 LTS with XFCE 4.8.  I installed OpenJDK 7, and then had to use a terminal to execute the Minecraft.jar file.  OpenJDK 7 was able to launch Minecraft, but when I logged into my account (after some years) and clicked Play, it appears to do some update, but then will spontaneously close and relaunch on its own in 5 seconds; clicking Play again yields the same results.

Any ideas why this is happening? Let me know if you need more info--thanks!


I'm also not opposed with someone with a working-Minecraft configuration of Ubuntu sharing with me what they use and I'll figure out how to install it ;)

---

### Post by mastablasta on 2014-05-29
hmm it seems my reply got lost...

so i will try to do it again: in previous versions of minecraft a few extra libraries were needed. they shouldnt' be necessary with newer version but i guess it wouldnt' hurt to expore a bit.

also i use oracle java.

what is your command line to launch it? how much ram do you have? is there any error message in terminal?

---

### Post by efflandt on 2014-05-31
If you have not played minecraft in some years, you may need to migrate your account into a mojang account, that will use your e-mail address and password, instead of minecraft username and password. To migrate your account see [https://account.mojang.com/migrate](https://account.mojang.com/migrate)

Otherwise any error messages in terminal launched from or logs in ~/.minecraft/ or ~/.minecraft/logs/ may help troubleshoot.

I have been running minecraft since. beta in 64-bit Ubuntu, currently Ubuntu 12.04 with default unity desktop using openjdk-7-jre and nvidia graphics drivers. Minimally I have run it on a 1 GHz 2 core tablet PC with 2 GB RAM and ATI HD graphics that boots Linux from SD card. On that Lubuntu (lxde desktop) is a bit faster than Ubuntu with unity.

---

### Post by wolflint on 2014-06-12
Does the game close or the launcher?

---

