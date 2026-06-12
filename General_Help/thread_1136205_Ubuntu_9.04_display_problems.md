---
title: "Ubuntu 9.04 display problems"
date: 2009-04-24
forum: General Help
---

### Post by sirspam28 on 2009-04-24
Ok, so I just installed jaunty as a dual boot and it worked perfectly, going through the updates and installed the nvidea 180 restricted drivers, but now when I load i have no display, if just shows a text loading screen that flickers at the battery check.  crtl+alt+f2 allows me to log in in the terminal, but still no display, and when i try to open a graphical program(i.e. firefox), it error's no display specified.  I am running two 9800gtx's in sli as my gpus.  Help?   

also, very little knowledge of linux

---

### Post by Kareeser on 2009-04-24
Hi sirspam28... can you copy and paste the error messages you get when you run the command "startx"?

Also, can you elaborate what you mean with "flickers at the battery check"?

In the meantime, I'd recommend manually installing your graphics card drivers directly from the NVIDIA website. 180.51 works fine for me :)

---

### Post by sirspam28 on 2009-04-24
Kareeser

Thanks for the quick response, how do I go about obtaining and installing that driver from the command line?



edit:

the flickers at battery check i mean that after the splash screen with the load bar it goes to a text screen in the format of
* starting ...    [ok]
til
*checking battery state... [ok]
at this point the screen flickers thrice, then just stays here indefinatly


also
startx error msg

xorg-server 2:1.6.0-oubuntu14
(==) Logfile: "/var/log/Xorg.0.log", Time: Fri Apr 24 20:02:59 2009
(==) Using configfile: "/etc/X11/xorg.cong"
Primary device not in PCI
(EE) No devices detected
Fatal Server Error:
no screens found
ddxSigGiveUp: Closing Log
giving up.
xinit: No such file or directory (errno2): unable to connect to x server
xinit: No such process (errno3): Server error

---

### Post by Windsnake21 on 2009-04-25
I am having the same problem here with 2 Nvidia GeForce 8600GT cards which can run in SLI mode. I have a 22" GNR monitor.

---

### Post by sirspam28 on 2009-04-25
Ok, I am at my wits end trying to get these drivers to work, and I have no idea how to do it.  Installing both 177 and 180.51 through the manager in Ubuntu fails, downloading and installing off the website and running the nvidia-config files fail, no matter what I do, as soon as I install the driver I lose all gui.  I would really like some help or at least somebody to tell me this is a bug and Im bangin my head against the wall.  And if that is the case, how do I roll back x to pre driver install so I can get my gui back?

---

### Post by ed-koala on 2009-04-26
I am having the exact same issue.  It was hell getting these to work in Intrepid for me, and now it's back.  Please, someone help!

---

### Post by Kareeser on 2009-04-26
Bumping for the OP's sake.

---

### Post by sirspam28 on 2009-04-26
Ok doke, so quitting gdm, then uninstalling the NVIDIA driver run package then rebooting into recovery and running xfix has got my gui back, but still no driver support?  does anyone know how to install these things?

---

### Post by hansdown on 2009-04-26
Hi sirspam28.

I'm not sure if this will help, given all the recent posts concerning problems with nvidia.

[http://www.detector-pro.com/2009/04/how-to-install-nvidia-linux-display.html](http://www.detector-pro.com/2009/04/how-to-install-nvidia-linux-display.html)

---

### Post by sirspam28 on 2009-04-26
No go, now gui is down again, even after xfix, thanks for the reply though!

---

### Post by Morientes on 2009-04-26
I also have this problem.

---

### Post by Morientes on 2009-04-27
I have figured my problem out!

It was a bit of a DOH point. I have a TV connected to  my other DVI port and it simply output to this instead.

So I just turned it on and on that changed in nvidia-settings to output to my computer monitor instead.

Perhaps this can help someone here...

---

### Post by mlejayne on 2009-04-27
Hi, I'm running Jaunty on a resurrected computer that in it's past life had a TV output card. I'm experiencing the same problem. Could you tell me how you changed the output in the xorg file? 

I'm pretty new at this. Thanks for your help.

---

### Post by Morientes on 2009-04-29
Change it like in this post: [http://ubuntuforums.org/showpost.php?p=7156764&postcount=15](http://ubuntuforums.org/showpost.php?p=7156764&postcount=15)

---

### Post by AryanAngel on 2009-05-09
I am having the same issue, nothing seems to work! Figure it out sirspam28?

---

### Post by rufusthedeadcat on 2009-05-19
Having the same problem. Solutions thus far presented have had no effect. Any more suggestions folks?

---

### Post by jober on 2009-05-27
I am also seeing this same problem. I have dual nVidia GeForce 9500 GT cards. Both were working fine, with output to 4 monitors for a week or so.

I restarted the system to move some cables around and ever since, it's been failing.

I've uninstalled the packages via APT and installed the nvidia binary (180.51) and that hasn't improved things.

What is strange, is that it works SOMETIMES. If I reboot, it hangs on starting GDM, displaying the: "Checking battery state..." message (This is actually GDM hanging, the battery state check is fine).

I have a working xorg.conf, which I know, because if I drop to a different TTY and login to the system via terminal, I can do a /etc/init.d/gdm stop ; sleep 30 ; /etc/init.d/gdm start (the sleep 30 seems to work a litlte bit more consistently).

I guess at this point, I am running out of options. When the same exact commands work 1 out of every 5 or 10 times, it doesn't really make sense to me, that it's a configuration problem. If it is, I am not sure where to turn next. I'd welcome any feedback on this, or any new angles to come at this. I really need to get this system working again. I put a ton of time into configuring it, so I am also hoping to avoid a reinstall (and I don't even know if that would provide any better luck).

One other note, is that I see that mesa-utils was updated in the past 30 days, which is the only one that sticks out as being graphics related.

Thanks

---

### Post by badtazz72 on 2009-05-28
i also have same problem so I know im not alone there must be a fix](*,)

---

### Post by jober on 2009-05-29
After much banging my head on the wall, I did finally figure out a solution. Xinerama was the source of my problem. If I disabled that, it worked properly.

Except I have 2 video cards and 4 screens, so I wanted to use Xinerama and that was kind of critical to me.

After about 100 reboots and xorg.conf crashes and breaks. I finally stumbled onto a forum that simply helped me figure out that if I do this, I can't stack one set of monitors above the other, such as:

1 2
3 4

This would cause the crashes and much headache.

If I did 1 2 3 4 it would work, that's how I figured it out.

I changed my config of monitors to be:

3 2
4 1

That worked and I am off to the races.

Thanks and I hope this helps. If you have more questions on this, I have tried almost everything, so I would hopefully be able to help =)

---

### Post by NeoDude007 on 2009-06-12
I am also having the issue where everything is fine after a fresh Ubuntu 9.04 install. I run updates, restart just to see if that screws it up, then install the god forsaken 180 Nvidia drivers that say "recommended" and next restart results in the PC hanging there on that *Checking Battery State... thing.... what the F...

Is it an SLI thing? I really don't want to take out one of my video cards (SLI 8800GT) because it is a pain and I use SLI for gaming in Vista. Seems I am about the 3rd person at least on this topic to be SLI...

---

### Post by Isaacgallegos on 2009-10-10
I've been having this for 2 months now and yet there is no solution. 

Someone please help!!!!!!!!!!!!

---

### Post by Isaacgallegos on 2009-10-11
bump

---

### Post by hpprinter100 on 2009-10-11
bump i have 9500gt in in sli and i am getting the checking batter state... hang :S

---

### Post by Isaacgallegos on 2009-10-11
Bump!

---

### Post by Isaacgallegos on 2009-10-11
Bump!!!!!!!!!!!!!

---

### Post by hpprinter100 on 2009-10-11
im gonna do a fresh installl and then try installing the driver after doing all of this 

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by Isaacgallegos on 2009-10-11
I think this problem has something to do with using Xinerama with 2 video cards. 

God this is such a mess...

---

### Post by Isaacgallegos on 2009-10-11
*bump*
According to this I need matching video cards. My video cards don't match exactly but they're both using the same driver. It just works on xp. It should just work in ubuntu. 
[http://www.nvnews.net/vbulletin/showthread.php?t=134148](http://www.nvnews.net/vbulletin/showthread.php?t=134148)

---

### Post by jober on 2009-10-11
Well, I finally got consistency out of 2 video cards and to get the other monitors working (6 total), I broke down and bought a Matrox TripleHead2Go. That product rocks and now I have all 6 working in a single configuration such as:

2a 2b 2c
3   1  4

The only bummer is that I can't go to any higher resolution than 19" monitors across the top row.

I hope that helps.

---

### Post by hpprinter100 on 2009-10-12
i am going to get rid of my sli and buy a single 896mb card instead hopefully that will work :D

---

### Post by Isaacgallegos on 2009-10-12
Cool. I'm gonna buy a sw 500 cal and shoot this thing.

---

