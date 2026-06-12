---
title: "How to install the 0.8.5 patch of Open Arena on 0.8.1"
date: 2010-06-22
forum: Gaming &amp; Leisure
---

### Post by Revolutionary101 on 2010-06-22
This isn't a question. It is more of a tutorial for those who had difficulties finding help for this. I now know how easy it is an I want to share my knowledge. This tutorial assumes that you already have Open Arena installed.

To get the 0.8.5 patch go here: [http://openarena.ws/request.php?3](http://openarena.ws/request.php?3)

Once you download the zip file, open it up. Inside the .zip file go to /openarena-0.8.1/baseoa. In there you will find a file named pak6-patch085.pk3

Once you have found this file, copy and paste it into the folder /usr/share/games/openarena/baseoa. After you paste it in there the install is complete.

Just run Open Arena and you will see the new things that come with the patch. I hope you all enjoy!

---

### Post by Warbandit on 2010-06-22
Is this a game and if it is where can I download it?

---

### Post by Revolutionary101 on 2010-06-22
Yes this is a FPS game. You can download it by going to Applications>Ubuntu Software Center. Then search for Open Arena. When it pops up just click on install to download and install it.

I personally think it is one of the greatest games available for Linux.

---

### Post by PC_load_letter on 2010-07-19
Thanks for the info, much appreciated. Why the heck this info is not given in the readme file? Anyway, a GREAT game just got better.

---

### Post by checoimg on 2010-12-25
Thnks A lot!!!! :)

---

### Post by checoimg on 2010-12-25
If you guys have some time to help here:
[http://ubuntuforums.org/showthread.php?p=10279169#post10279169](http://ubuntuforums.org/showthread.php?p=10279169#post10279169)

the patched worked but this problem didn't fix

---

### Post by GhostRevenant on 2011-05-31
> **Revolutionary101 said:**
> 
Once you have found this file, copy and paste it into the folder /usr/share/games/openarena/baseoa. After you paste it in there the install is complete.

Just run Open Arena and you will see the new things that come with the patch. I hope you all enjoy!

So, I found the folder, but when I tried to copy it over, it told me, "Permission denied".  Considering that I own the computer, I don't see a reason that this should happen.  Any ideas on what to do?

---

### Post by stealz on 2011-08-08
you need to show your computer that you have those rights.

in this case i think the easiest way is to unzip your patch in your download directory, and then start a terminal with ctrl+alt+T
then type 

gksu nautilus

after this, you will be prompted for your admin password. use the window to locate the download directory, copy the pak6-patch085.pk3, navigate to and paste it in the installation directory (see above)

---

