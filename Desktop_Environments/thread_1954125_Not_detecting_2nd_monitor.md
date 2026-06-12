---
title: "Not detecting 2nd monitor"
date: 2012-04-07
forum: Desktop Environments
---

### Post by Eirreann on 2012-04-07
Okay, so I'm very new to Ubuntu; I installed it yesterday and since I installed it and applied the 173 Driver+updates (so that I could use Ubuntu non-2D) my laptop hasn't been detecting my external monitor, which I use because my laptop's screen is pretty screwed up (dis-coloured pixels all over the place). So I've been scouring Google but since I'm new at this most of the instructions on how to fix this issue don't make any sense to me.
I did try going into Nvidia settings (I am running an GeForce FX Go5200, btw) and accessing X Server Display Configuration, but when I open that up it says:
"Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0. "

And in the "Display" settings it labels my laptop's display as "Unknown" and doesn't even register that I have an external monitor plugged in.
I'm dual-booting Ubuntu alongside Windows XP (if that helps at all). And I really need the external monitor!

Thanks in advance!

(Sorry if you see this thread in other forums, but since the initial thread doesn't seem to be getting much attention in the "General forum", I decided to try posting it other places.)

---

### Post by bobman321123 on 2012-04-07
I'd just wait for the new version to be released. 
It's coming out on April 26th, and it's said to have MUCH better dual monitor support. 
It's only 20 days away, can you wait that long?

---

### Post by Eirreann on 2012-04-07
> **bobman321123 said:**
> I'd just wait for the new version to be released. 
It's coming out on April 26th, and it's said to have MUCH better dual monitor support. 
It's only 20 days away, can you wait that long?

Do you mean 12.04 (or whatever number it is?)  So soon?  Man, I wish I had known that, haha!  Will they be making a Windows Installer for that one as well?

---

### Post by texpat on 2012-04-07
There are 2 NVIDIA drivers available. Make sure you have the one that says "post-release updates".

---

### Post by Eirreann on 2012-04-07
> **texpat said:**
> There are 2 NVIDIA drivers available. Make sure you have the one that says "post-release updates".

I'm pretty sure that's the one I'm already running, but I'll double-check...

---

### Post by bobman321123 on 2012-04-07
> **Eirreann said:**
> Do you mean 12.04 (or whatever number it is?)  So soon?  Man, I wish I had known that, haha!  Will they be making a Windows Installer for that one as well?

I'm not sure if they will or not.... 
But yes, It's 12.04. You can get it right now if you want, but I warn you, it is slightly unstable :P

EDIT: I'm typing this on 12.04 right now. It works well enough for me.

---

### Post by Eirreann on 2012-04-07
> **bobman321123 said:**
> I'm not sure if they will or not.... 
But yes, It's 12.04. You can get it right now if you want, but I warn you, it is slightly unstable :P

EDIT: I'm typing this on 12.04 right now. It works well enough for me.

I really hope that they do, because installing dual-boot from a disc doesn't work on my laptop, for some reason... something to do with a mistake I made while partitioning a dual-boot with Windows 7 (which ended up failing epically, but I digress).
I'll just experiment with the drivers for the time being and hope for the best.  (I love your signature, by the way)

---

### Post by bobman321123 on 2012-04-07
> **Eirreann said:**
> (I love your signature, by the way)

Haha, thanks :P
Take it if you like.

---

### Post by Eirreann on 2012-04-07
> **texpat said:**
> There are 2 NVIDIA drivers available. Make sure you have the one that says "post-release updates".

Okay, I checked and it looks like I'm running the "NVIDIA Accelerated Graphics Driver (post-release updates)(version 173-updates)" and with it I am having this problem with my external monitor.  It looks like there is another driver available that is post-release updates but it is "(version 96-updates)".  I'm going to give that one a try now, and if that doesn't work then I'll still have a problem, I guess, haha!
I wonder why Ubuntu hasn't released a fix for this, I'm one of quite a few people having this problem, it seems... just about everyone with an Nvidia card, that is.

---

### Post by Eirreann on 2012-04-07
YES!!!  It seems that rolling back to the version 96 drivers did the trick!!!!
However, one worrying thing; my laptop monitor has completely shut down and is entirely black, and upon booting Ubuntu I got a huge error message that said:
none of the selected modes were compatible with the possible modes:
[I]Trying modes for CRTC 294
CRTC 294: trying mode 1920x1080@50Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1920x1080@51Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1680x1050@52Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1680x1050@53Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1600x1024@54Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1440x900@55Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1400x1050@56Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1400x1050@57Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1400x1050@58Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1360x768@59Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1360x768@60Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1280x1024@61Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1280x1024@62Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1280x960@63Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1152x864@64Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1152x864@65Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1152x864@66Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1152x864@67Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1024x768@68Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1024x768@69Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 1024x768@70Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 960x600@71Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 960x540@72Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 896x672@73Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 840x525@74Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 840x525@75Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 840x525@76Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 840x525@77Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 832x624@78Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x600@79Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x600@80Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x600@81Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x600@82Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x600@83Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x600@84Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 800x512@85Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 720x450@86Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 680x384@87Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 680x384@88Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 640x512@89Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 640x512@90Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 640x480@91Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 640x480@92Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 640x480@93Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 640x480@94Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 576x432@95Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 576x432@96Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 576x432@97Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 576x432@98Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 512x384@99Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 512x384@100Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 512x384@101Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 416x312@102Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 400x300@103Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 400x300@104Hz with output at 1280x800@50Hz (pass 0)
CRTC 294: trying mode 400x300@105Hz with output at 1280x800@50Hz (pass 0)[/I]

Is that anything that I need to worry about???

In any case, I'm marking this thread as "solved".

---

### Post by VitasLoWang on 2012-11-12
I have the same problem with these messages!
I managed to setup twinview with nvidia-current driver so my external monitor works, but every time I boot up my ubuntu 12.04 the resolution is wrong and I get those errors, but after few seconds it is fixed so the resolution on external and also internal display is right.
The problem starts when I startup the computer without external monitor connected. Then it is really screwed up - the notification area and the welcome window opened on the desktop are stretched, mouse cursor moves only verticaly I get spammed by those errors and it does not get fixed by itself. If I manage to somehow go to nvidia-settings I can change the resolution from auto to 1600*900 and it is fixed, but the mouse cursor still does not work so I have to restart anyway.
Win+P key does not work as it used to on Ubuntu 11.04. I Guess I had the nouveau driver back then...

EDIT: Great and now the login dialog does not appear at all! I type LUKS password and then the screen gets stuck. Damn :( Cannot even switch to text console. If I press escape in the LUKS prompt it changes from text to graphical and ends up with text login with no X server. So what now?

When I try sudo lightdm it starts something but gets stuck on "checking battery state". After switching to Alt+F5 console I can login and do startx and I get Fatal server error: no screens found.
Error on line 7 when parsing xorg.conf, so the nvidia.-settings put some nonsense there probably...

Will try [http://askubuntu.com/questions/167000/xorg-server-configuration-fail-no-screens-detected](http://askubuntu.com/questions/167000/xorg-server-configuration-fail-no-screens-detected) when I get another network cable ...

---

