---
title: "latest Nvidia update and Gnome Shell problem"
date: 2012-04-14
forum: Desktop Environments
---

### Post by OldSmoky2 on 2012-04-14
Gnome Shell in Natty isn't working properly anymore and I suspect an April 11 NVIDIA update may be the culprit. I have been using Gnome 3 Shell with Ubuntu 11.10 since December with no problems. It's been very smooth. But in the last couple days I've had three instances in which the Gnome Shell panel suddenly became distorted - the first time, all the text became unreadable, just strange blocks and a few symbols. The panel also changed from its normal black color to a whitish-gray.
The second time the panel turned whitish-gray with no text at all. The third time the panel changed to a small rectangle about an inch long, was whitish-gray and was displayed left of center a half-inch or so below the top of the screen. All of these distortions occurred after I had been using the computer for anywhere from 2 to 12 hours, and the functions in the panel seem to be there in all instances. Though I can't read any text, if I click on the right end of what's left of the panel, I get a dropdown menu box, also unreadable, and can then click at the bottom to restart or shutdown, where I would normally click.
I think this is tied to the NVIDIA 173.14.30-0ubuntu5.1 update that came from Ubuntu April 11. I say that after searching for an answer and finding that quite a few people have had problems with Gnome Shell and older NVIDIA cards in Natty as well as Linux Mint. As I said, I have not until now so I didn't know that. And I'm not a techie and I'm not positive that the NVIDIA update the other day is the problem. It just seems to be the best suspect at this point since everything worked fine before that.
If that is it, I'm not real hopeful I'll be able to fix this after reading about other people's NVIDIA/Mutter/Gnome Shell problems, which is a shame since I like the Natty/Gnome Shell combo a lot. But I thought it would be worth a try here to see if anyone else might have an answer.
FYI, I'm using a 6-year-old Dell DXP061 with a NVIDIA GeForce 7900 card. At the moment, I've booted into Kubuntu 11.10, which I have on a separate partition. It also got the NVIDIA update but seems to be fine as always. I am going to restart, though, and boot up in Unity instead of Gnome Shell to make sure the problem is just confined to Gnome Shell.
Anyway, anyone have any suggestions?

---

### Post by theknightlinux on 2012-04-14
Hello. Have you tried going back to the drivers you had before, or using the post-release updates from nvidia?

---

### Post by OldSmoky2 on 2012-04-14
> **theknightlinux said:**
> Hello. Have you tried going back to the drivers you had before, or using the post-release updates from nvidia?

No, I looked up the update and found it was a security update supplied by NVIDIA, not a new driver. It just patched a hole that could have allowed an attacker to get root privileges.

---

### Post by theknightlinux on 2012-04-14
Is Unity doing fine?

---

### Post by theknightlinux on 2012-04-14
> **OldSmoky2 said:**
> No, I looked up the update and found it was a security update supplied by NVIDIA, not a new driver. It just patched a hole that could have allowed an attacker to get root privileges.

What I would recommend for you to do is to go to additional drivers and downgrade to a post-release update to see if they work.

---

### Post by theknightlinux on 2012-04-14
Or you might want to upgrade to 12.04 or wait till the 26 and then update the Gnome shell.

---

### Post by OldSmoky2 on 2012-04-14
> **theknightlinux said:**
> Is Unity doing fine?

Yes, Unity is working very well. I even installed MyUnity a while ago and have been tweaking it some. It's fine - I was getting pretty used to Gnome Shell though. But, yeah, it's not like the end of the world. If Unity continues to work without problems, then I would say that confirms that for some reason I just started having the same problems other people have had with Mutter/Gnome 3 Shell and older NVIDIA cards. And there doesn't seem to be any solid solution for that.

---

### Post by OldSmoky2 on 2012-04-14
> **theknightlinux said:**
> Or you might want to upgrade to 12.04 or wait till the 26 and then update the Gnome shell.

Yep, may just do that. It still might not resolve the Mutter/Gnome 3 Shell/old NVIDIA problem.

---

### Post by TheBigW on 2012-04-15
I just wanted to confirm that I have similar problems: even a bit worse: some of the OpenGL dependend SW seems to have problems after the update (e.g. Alien Arena crashes after some time, Superttuxcard too), worse is that I can only login into Ubuntu 2D now, normal login just hangs. I have a old Nvidia 8900 GTS. Same for me : I will update to 12.04 and just hope that fixes my issues...

---

### Post by bogan on 2012-04-15
Hi! **all**,
I also had problems following the recent nvidia-current update and cured it by running:```
sudo nvidia-installer -f 
```from a text terminal [tty - press Ctrl+Alt+F1 or F2].

This un-installs the previous driver and downloads and installs the latest version 295.40 which is recommended for both the 7xxx series and 88xxGTS series cards, as well as GT5xx series. [The 8900GTS is not listed on the NVIDIA Downloads Search function.]

I suspect the problem comes from the update manager installing the updated driver whilst the XServer is running, Nvidia strongly warn it should not.

Chao!, **bogan**.

---

### Post by OldSmoky2 on 2012-04-15
> **bogan said:**
> Hi! **all**,
I also had problems following the recent nvidia-current update and cured it by running:```
sudo nvidia-installer -f 
```from a text terminal [tty - press Ctrl+Alt+F1 or F2].

This un-installs the previous driver and downloads and installs the latest version 295.40 which is recommended for both the 7xxx series and 88xxGTS series cards, as well as GT5xx series. [The 8900GTS is not listed on the NVIDIA Downloads Search function.]

I suspect the problem comes from the update manager installing the updated driver whilst the XServer is running, Nvidia strongly warn it should not.

Chao!, **bogan**.

Thanks, this looks promising. (I did a little more reading about it.) One question, though: Should I shut down the XServer and run the command, then restart X?

---

### Post by bogan on 2012-04-16
Hi!, oldsmoky**2**,

You Posted:>   One question, though: Should I shut down the XServer and run the command, then restart X? Yes, Nvidia-installer will refuse to install if Xserver is running.
Either boot to a text terminal, open one by >  [tty - press Ctrl+Alt+F1 or F2] or Ctrl+Alt+T from a GUI screen and run: ```
sudo service lightdm stop  # 'gdm' instead of 'lightdm' if <11.10
 sudo service lightdm start  # afterwards to return to GUI, or reboot.
``` If you get " nvidia-installer: command not found", you will need to download the .run file from nvidia.com/downloads, make it executable and run it with 'sh'.

Chao! **bogan**.

---

### Post by OldSmoky2 on 2012-04-17
Just FYI - I'm holding off on doing anything about this for the moment after finding out that the NVIDIA driver update itself is most likely the cause of the problems. You can read about it at [http://www.phoronix.com/vr.php?view=MTA4ODc](http://www.phoronix.com/vr.php?view=MTA4ODc) ... NVIDIA says they are working on a fix. For me, it's only an issue when I'm running Ubuntu 11.10. I did the same update earlier this week on my Kubuntu 11.10 partition but I've been running it for more than two days now with no problems at all. The issues people are having affect pre-G80 cards, like mine, in multiple Linux distros and are described as "weird" and varied, so it's no surprise that Ubuntu (which I use Gnome Shell on) is affected but not Kubuntu. (I can't say that I ran Unity long enough to know if it's affected, too.) Since I can access my files on both partitions when running Kubuntu, it's not a huge deal to just wait for the NVIDIA fix.
That said, I'm going to mark this as solved.

---

### Post by aalhamer on 2012-04-17
Download driver from Nvidia Website

While on desktop hold [ctrl + alt + F1]

log in

Go to download directory [cd /home/usernamer/folder] case-sensitive*
Type [sudo service lightdm stop] to terminate Xserver
Type [ls] to view whats in the current directory

Type the file name as seen in the directory in the following manner case-sensitive* [sudo sh ./NVIDIA-Linux-x86-295.40.run]

After accepting terms and conditions you with be asked to setup xConfig just choose [yes] to auto config unless you want to customize your config settings.
After that you should be back at terminal

type [sudo service lightdm start] to initiate Xserver
which should bring you back to the log in screen

log in and restart
you might need to download Unity from Software center but all should be good!!

hope it helps

---

### Post by OldSmoky2 on 2012-04-20
Thanks.. looked into it but NVIDIA is specifically telling people not to use 295.40 with GeForce 7 series cards right now because of problems on Linux systems. (See [http://www.nvnews.net/vbulletin/showthread.php?p=2546510#post2546510](http://www.nvnews.net/vbulletin/showthread.php?p=2546510#post2546510) ).
There is a bug report filed at NVIDIA as well.
I did run my system with Ubuntu 11.10 and Unity yesterday for a few hours - it was fine for a while but then it went very bad suddenly, with the launcher and the panel in particular becoming very distorted. So at least I know the issue isn't just with Mutter (see above - I was running Gnome 3 Shell earlier).
I'm still inclined to wait for 12.04 at this point and see what happens. As I mentioned above, I have Kubuntu 11.10 on a separate partition and even though it got the same update that started these problems on Ubuntu 11.10, it's been running perfectly. So at least I am not pressed to fix this so quickly since I can access my files on both partitions.

---

### Post by TheBigW on 2012-05-15
looks like the issue still exists for me. I switched to 12.04 - same issue. I tried several NVIDIA driver - same issue. I switched to noveau now: everything seems to be fine except only Ubuntu 2D is working (do not really care). 3D Performance e.g. for alien arena is still acceptable. I will survive until the nvidia issue is finally fixed or by an ATI card inbetween :)

---

