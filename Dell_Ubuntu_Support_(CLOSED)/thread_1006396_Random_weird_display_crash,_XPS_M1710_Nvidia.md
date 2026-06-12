---
title: "Random weird display crash, XPS M1710 Nvidia"
date: 2008-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wecucho on 2008-12-09
Hi, i have this annoying problem.

[http://ubuntuforums.org/showthread.php?p=5961719#poststop](http://ubuntuforums.org/showthread.php?p=5961719#poststop)

My screen turns into a garbled grey thing, even if i switch tty or reboot the X server, only if i reboot the machine i get my clean display again, i dont know what is causing this... anyone has a similar problem or tip on this ?

a few updates back in time solved my problem for two weeks (i dont have another explanation for that) but it just bugged again.

---

### Post by andelo on 2008-12-13
I'm experiencing the exact same thing on my XPS M1710 (with Geforce Go 7900 GTX) running Ubuntu 8.10

Tried upgrading to the latest nvidia beta driver out of desperation (Linux Display Driver Version 180.06 BETA), however it was only running fine for a few days until the next crash.

I really don't feel like reverting back to 8.04, so switched back to Vista for the time being :cry:

---

### Post by zeke7237 on 2008-12-21
I've got this problem .. just installed ubuntu after a long love-hate relationship with gentoo .. looking for solutions to try ..

---

### Post by galenparker on 2008-12-26
I too am having the same problem.

Dell M1710 Laptop. Geforce 7950 gtx.


It *kinda* feels like an overheat problem due to the intermittent occurrence of it. However most of the time the situation happens during a non intensive activity. Checking temperature values also doesnt show anything out of the ordinary.

Furthermore, an immediate reboot (must be done by pressing the power/restart) button fixes the issue.

Restarting gnome or dropping to terminal yields no results.

I can't help but feel its a ubuntu-driver issue but cant give instructions on how to consistently replicate the fault.

Any input/help wouldbe great and i'm happy to provide the output of various debugging commands.

Oh also... the computer doesnt "lock up" just the screen becomes this garbled mess. You can still trigger actions (like ctrl-alt-backspace) but the display is still borked. 

Potentially tho.. if a decent set of debug commands could be entered it would be possible to "log to file" the output of any of these commands while the problem is present.

Thanks
Galen

---

### Post by andelo on 2008-12-28
Noticed this issue was also mentioned here:

[INDENT]Laptop Overheating?
[http://ubuntuforums.org/showthread.php?t=811001](http://ubuntuforums.org/showthread.php?t=811001)[/INDENT]

Did anyone make any inroads into this?

Also, has anyone been running with the standard NV driver & compiz disabled to see if it re-occurs? I've disabled compiz (aka desktop effects) with the same result. Haven't tried the NV driver though... but who wants to run their PC's without the desktop effects anyway?? :(

---

### Post by mascer on 2009-01-01
I have the same problem on my m1710...especially with SecondLife in ultra high graphics mode. Looks like the v96 Nvidia driver works best for me combined with disabled desktop features...only 1 or 2 crashes/blurs every 12 hours. Now waiting till they release a new driver :confused:

I also installed the Dell-thingies..works great to get an idea of heating versus crashes. See: [http://ubuntuforums.org/showthread.php?t=896232&highlight=high+temperature+gpu+nvidia]("http://ubuntuforums.org/showthread.php?t=896232&highlight=high+temperature+gpu+nvidia")

---

### Post by lokmij on 2009-01-04
Umm.... so what driver are you using? for the XPS m1710?  how do i know what video card i have and where do i get the driver for ubuntu?  I have Ubuntu 8.10
                - the Intrepid Ibex - released in October 2008.
				
ohh.. and I like the fancy desktop thingies! but when i enabled them its when the display would start to randomly crash, and i really don't want to disable them... there has to be a way around it..

---

### Post by andelo on 2009-01-04
I've been having this issue with the current recommended nvidia driver 177.80. If you run nvidia-settings or go System -> Administration -> Nvidia X Server Settings, it will tell you the version of driver you're using.

Also, I've found a workaround for this issue. It may not be the most elegant, but it sure beats a reboot. Just close the lid of your laptop and open it back again ;)

Also just notice a new beta driver 180.17 that was released December 19th containing loads of bug fixes. Have anyone tried this yet?  Otherwise I'll install this when I can and post back the results.

Cheers.

---

### Post by mmoralls on 2009-01-07
I've installed the 180.17 beta driver on my XPS M1710 and it works.:D Aside from the occasional 1/4 second blink on the screen I've not had a major crash like before where I had to reboot. I can run AWN and switch desktops but haven't tried any Compiz stuff yet.

Can't wait for the full version.

---

### Post by stoneybridge on 2009-01-15
wow has this been sorted?!! i was having the same prob with my xps m1710 my card is a 7950 gtx, gonna have a go with these new drivers as soon as.....

---

### Post by HnKDKS on 2009-01-15
I have the 7900 GTX with the same problem. Has the new non beta 180.22 drivers from NVidia been tested? I know it was released on the 08 Jan 2009 but it's not showing up in my restricted drivers. I could download them and install them but what's the point if they are going to show up in the update soon.

---

### Post by stoneybridge on 2009-01-15
well finally got the new 180.22 drivers to install. no screen coruption seems all fine and dandy. had the screen flashing prob too but locked the screen refresh rate to 60hz instead of the default "auto" and it went away:P

---

### Post by stoneybridge on 2009-01-15
dam its just done it again..and again:confused:

---

### Post by voidproton on 2009-01-19
hows the gpu temperature ?

---

### Post by stoneybridge on 2009-01-21
temp is fine bout 60c when idle just had a play at alien arena for 10 mins, didn't go above 70, it's more or less sorted now, it's done it twice in about 40 hours of using the pc, left "video blitter adaptor settings,   sync to vblank" unticked and it seems to have done the trick,

the new 180.22 drivers made a huge dfference

---

### Post by nicknefarious on 2009-01-23
I have an XPS M1530, with NVidia 6800GT and have installed NVidia 180.22, Ubuntu 8.10 64-bit and I have what sounds like exactly the same problem. I have a feeling 180.22 is good and it's an Ubuntu problem, but just a feeling.

[http://ubuntuforums.org/showthread.php?t=1047977]("http://ubuntuforums.org/showthread.php?t=1047977")

I have searched and searched but can't find anything on this except here ofcourse. Anyone know more? It is very difficult to replicate and is extremely random (see above link).

---

### Post by stoneybridge on 2009-01-25
[[IMG]http://img217.imageshack.us/img217/3046/image161dq0.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=image161dq0.jpg)

this is what it looks like on my laptop, it hasn't done it for ages now so theese are my settings on 8.10 32bit  my screen resolution is 1920x1200 60hz (locked not auto) video blitter adaptor settings vblank unchecked everything else default

i think cutting down on all the fancy stuff on compiz help too

the last time it did it was as soon as displaying some visulisations on totem, playing an mp3, may of been a coincidence? who knows... seems to do it alot under kde as well

---

### Post by wice on 2009-01-26
Still no real help on this one, googled since i started using Ubuntu :/

Got the 180.22 now atleast.. wich didnt help. Alltough it sais it fixes display corruption in the description on the driver for 6-7 serier GPU's.

Really wierd. No overheating at all, the lappy is not even warm.

Edit: exact same corruption as stoney, refering to the pic above.

---

### Post by wice on 2009-01-26
Had this problem for over a year or two now.

And now i've atleast got a temp fix.

If you've got a second display/tv out/etc.. then you could just press the function key on the laptop then switch back and forth to the display your using. And it dissapears. That i've known for a long time.

But now when i just got mad for the 300th time it came up(the annoying screen flicker..), i just closed the lid with the option "blank screen on lid close" applied and then opened and it's fine again.

So no need to restart the computer or whatever you usually do. Hope this helps some people who looses data when they need to reboot the computer.

And for the record i still think it's something with the built in display manager displaying 50/51/52Hz and the nvidia-settings panel 60Hz as default, but no idea really. Not that good with hardware and ubuntu combined.

---

### Post by [Neurotic] on 2009-01-26
Well at least I know it's not just me! :D

That actually makes me feel better.

I've attached a picture of my screen doing exactly the same thing.

I've also got a dell XPS M1710.

I've found I can ctrl+alt+f1 to console to resolve the problem these days, although it can take a couple of attempts to get to the console, but it * does * work, eventually.

The bizarre thing is - it **never** happens, when I have my laptop connected to my 24" dell screen, and am running in twinview.  It only ever happens when I'm running as a single display.

Is there a bug filed for this somewhere? Sounds like we have a common enough issue.

---

### Post by stoneybridge on 2009-01-27
two more threads...

[http://www.nvnews.net/vbulletin/showthread.php?t=124186](http://www.nvnews.net/vbulletin/showthread.php?t=124186)

[http://www.nvnews.net/vbulletin/showthread.php?t=120896](http://www.nvnews.net/vbulletin/showthread.php?t=120896)

---

### Post by [Neurotic] on 2009-01-31
Seems to be a bug listed here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/270617/](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/270617/)

---

### Post by phenest on 2009-02-04
It was me that reported that bug originally. Does everyone here have the same laptop and video card? I have a Dell Precision M90 (same as a XPS M1710) with nVidia (obviously) Go 7950GTX. Maybe this is something Dell could help with.

EDIT: If anyone wants to help report this to nVidia, please use this link: [http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=44]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=44"). Read how to create a log first, so when it next crashes, send it to them. If everyone does this, they will have plenty of info to go on.

I also encourage everyone to set their screen to go blank when it's closed so you can use the lid close/open trick to reset the screen, then create the log and email it to nVidia.

---

### Post by phenest on 2009-02-04
In case anyone wants to know how to report this to nVidia:

When the crash occurs: either use the lid trick or reboot to restore your screen. Then run:
```
sudo nvidia-bug-report.sh
```
This creates an nvidia-bug-report.log file which you should email to nvidia: [email]linux-bugs@nvidia.com[/email] adding as much relevant information as you can, i.e. what computer, video card, and distro of Linux and anything else you can think of.

If anyone knows an easy way to contact Dell, post it here please.

EDIT: Could I ask everyone with this problem to post here what computer they have, video card model, and Linux distro (in case you're not using Ubuntu). I think we'll discover this is not distro specific or video card specific, but actually laptop specific.

---

### Post by elmargol on 2009-02-12
Same problem using 180.29

---

### Post by wice on 2009-03-12
> **phenest said:**
> In case anyone wants to know how to report this to nVidia:

When the crash occurs: either use the lid trick or reboot to restore your screen. Then run:
```
sudo nvidia-bug-report.sh
```
This creates an nvidia-bug-report.log file which you should email to nvidia: [email]linux-bugs@nvidia.com[/email] adding as much relevant information as you can, i.e. what computer, video card, and distro of Linux and anything else you can think of.

If anyone knows an easy way to contact Dell, post it here please.

EDIT: Could I ask everyone with this problem to post here what computer they have, video card model, and Linux distro (in case you're not using Ubuntu). I think we'll discover this is not distro specific or video card specific, but actually laptop specific.

I am on vista now so i'll tell you what i had before i switched back to Vista.

Dell M1710 with 7950 GTX 512MB with the driver version 180.22.

Still think it's "refreshrate/virtualsync/resolution" related becouse of the flicker is pretty much the same when using a "too" high resolution on an old CRT.

Actually next time i'm on ubuntu i will try if for example, 1600x1200 works. Would be appreciated if someone running ubuntu with this problem could try now ?

Thanks in advance!

Edit: maybe everyone doesnt know about the default resolution on M1710 wich is 1920x1200

// Wice

---

### Post by [Neurotic] on 2009-04-16
I've been running the nvidia 180.11 driver which came down updates a week or so ago, and have been running my laptop without my external monitor attached all morning (which is not usual for me), and have yet to see a display corruption.

Anyone else found that the display corruptions have gone away, or should I expect them to show up again at some point?

---

### Post by kjano on 2009-04-28
i am not sure if this is related but it could be interesting to you [https://bugs.launchpad.net/ubuntu/+bug/368659](https://bugs.launchpad.net/ubuntu/+bug/368659)

---

### Post by FreeSoul on 2009-04-28
Second thread I've replied to but in case you are tracking this one, here goes:

**CTRL-ALT-F10 seems to do the trick, appears to reset the monitor.** Though I haven't had the problem in weeks. (Under hardware drivers I am running V180 - I don't see "dots" saying which revision of 180...)

---

