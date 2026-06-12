---
title: "Compiz rotate cube"
date: 2009-06-27
forum: Desktop Environments
---

### Post by Gameguy411 on 2009-06-27
My friend got me in to Ubuntu and I love it. On his he has the compiz rotate cube activated so hitting certain keys moves to a new desktop as a 3d cube. I downloaded compiz from the add apps, selected desktop cube and rotate cube, but when i go to change screens it comes up as a flat wall and I can't fix that and make it so that it is an actualy cube. Help?

---

### Post by overdrank on 2009-06-27
> **Gameguy411 said:**
> My friend got me in to Ubuntu and I love it. On his he has the compiz rotate cube activated so hitting certain keys moves to a new desktop as a 3d cube. I downloaded compiz from the add apps, selected desktop cube and rotate cube, but when i go to change screens it comes up as a flat wall and I can't fix that and make it so that it is an actualy cube. Help?

Hi and welcome, you may look at the link in my signature on desktop effects FAQ's

---

### Post by enli on 2009-06-27
Type in terminal,

```
sudo aptitude install simple-ccsm
```

Then go to System -> Preferences -> Simple Compiz Configuration.. and configure the effects the way you like it. (I am on xp right now else I would have told the exact steps.)

Its for very basic configuration but it will get you started. After you are familiar play with "ccsm".

Welcome to the community.

---

### Post by Gameguy411 on 2009-06-27
Ah yes. I found the issue. Very n00b mistake, but I assumed my hand me down laptop could handle something so awesome. Nope, much to outdated graphics card. But thank you! I got it working on my desktop!

---

### Post by enli on 2009-06-27
There are few issues with Intel graphics cards. What is yours? Maybe you could get it working if you tell us.

---

### Post by Gameguy411 on 2009-06-27
>  Welcome to the community.
Ecstatic to be here :D. I tried that out, so far no good but i'm looking in to it.

---

### Post by Gameguy411 on 2009-06-27
The command line reads it as 
S3 inc. SuperSavage IX/C SDR (rev 05)

---

### Post by Gameguy411 on 2009-06-29
Is there some way around this problem or am I stuck with it as it is?

---

### Post by Gameguy411 on 2009-06-29
Hi, i'm wondering if there is a way to update graphics cards? I want to install the cube rotate on my older laptop but it just isn't working and I think it's because an outdated graophics card. I posted another thread here: [http://ubuntuforums.org/showthread.php?t=1198249&highlight=rotate+compiz+cube](http://ubuntuforums.org/showthread.php?t=1198249&highlight=rotate+compiz+cube) , i'm really just looking for in general ideas and solutions. Thank you in advance. As always help is greatly appreciated.

---

### Post by GUESS WHO525 on 2009-06-29
Well all i did was wait an then it said that there was a restricted driver called nvidia which means jealousy in spanish all i think you can do is wait!!!!:(

---

### Post by andrea000 on 2009-06-29
Run compiz in the terminal and post the output

---

### Post by Gameguy411 on 2009-06-29
> **andrea000 said:**
> Run compiz in the terminal and post the output
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by andrea000 on 2009-06-29
what video card do you have because there isn't a white listed
driver there you installed your driver from system administration
hardware drivers didn't you.You'll most likely have to un blacklist
it the out put doesn't show it as blacklisted i would run compiz check
first you can get that [here]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by overdrank on 2009-06-29
> **Gameguy411 said:**
> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

Hi and the S3 inc. SuperSavage  graphics are not supported well in linux and I do not believe it will support the desktop effects.

---

### Post by Gameguy411 on 2009-07-01
> **andrea000 said:**
> what video card do you have because there isn't a white listed
driver there you installed your driver from system administration
hardware drivers didn't you.You'll most likely have to un blacklist
it the out put doesn't show it as blacklisted i would run compiz check
first you can get that [here]("http://ubuntuforums.org/showthread.php?t=799070")
  Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         S3 Inc. SuperSavage IX/C SDR (rev 05)
 Driver in use:         savage
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards.





Does this mean i'm out of luck?

---

### Post by Mia1990 on 2009-07-02
I think so as overdrank said the SuperSavage cards are not very well supported on linux i came to ubuntu from from open solaris and they were not supported there very well at all

---

