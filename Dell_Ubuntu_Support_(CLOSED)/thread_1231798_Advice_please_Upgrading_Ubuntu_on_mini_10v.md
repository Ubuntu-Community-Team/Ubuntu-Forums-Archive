---
title: "Advice please: Upgrading Ubuntu on mini 10v"
date: 2009-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Noxwell on 2009-08-04
I've been using Dell's version of 8.04 and it has been a great experience but lately I have been running into scenarios where the software I want to use is only compatible with later versions of Ubuntu (like 9.04).  I would like to upgrade to a later version of Ubuntu but I am concerned with compatibility with the 10v (especially the trackpad and wireless).

What is the suggested approach?  Do I wait for Dell to announce their official version of 9.04 for the Dell mini 10v?  When and where would I get such information?

Is the preferred method to download the latest iso from ubuntu.com and hope that it is compatible with my netbook?  Do I then lose any hardware/driver support from Dell?  Are there linux patches available for the 10v from Dell that can be applied regardless of the distro or version?

Please forgive me as I am a complete noob and any sensible advice is appreciated.

Thanks

---

### Post by mikewhatever on 2009-08-05
I think the best possible approach is to try 9.04 running live from a usb stick. This way you can test both the touchpad and wireless and all the rest. Does Dell provide some kind of special multitouch functionality you don't want to loose? I think you should get everything working out of the box, as for the drivers, why do you think Dell provides something special that isn't available in 9.04?

---

### Post by Greasy_Larry on 2009-08-05
> **Noxwell said:**
> I've been using Dell's version of 8.04 and it has been a great experience but lately I have been running into scenarios where the software I want to use is only compatible with later versions of Ubuntu (like 9.04).  I would like to upgrade to a later version of Ubuntu but I am concerned with compatibility with the 10v (especially the trackpad and wireless).

What is the suggested approach?  Do I wait for Dell to announce their official version of 9.04 for the Dell mini 10v?  When and where would I get such information?

Is the preferred method to download the latest iso from ubuntu.com and hope that it is compatible with my netbook?  Do I then lose any hardware/driver support from Dell?  Are there linux patches available for the 10v from Dell that can be applied regardless of the distro or version?

Please forgive me as I am a complete noob and any sensible advice is appreciated.

Thanks

I just did the install, however I didnt have 8.04, I just started a dual boot system. As for problems, I did not have any. I only found Ubuntu Remix Netbook only in an .img format and had to make a bootable usb drive from the image, it was good skill to learn however, I plan on doing the same with XP. If you want to do just an update, I read a way to do it, but do not remember where. You will have to google it. I have a Mini10

---

### Post by snowpine on 2009-08-05
Dell will probably not offer an update from 8.04 any time soon, as 8.04 is the "long term support" version, supported through April 2011. Many Dell Mini users (including myself) have replaced the special "Dellbuntu" with a more recent, mainstream Linux release. 

Ubuntu 9.04 worked great on my Dell Mini 9 when I tested it. Not 100% sure about your Mini 10v; my suggestion is to test it in "live" mode from an external CD/USB for a while.

---

### Post by Noxwell on 2009-08-05
> **mikewhatever said:**
> I think the best possible approach is to try 9.04 running live from a usb stick. This way you can test both the touchpad and wireless and all the rest. Does Dell provide some kind of special multitouch functionality you don't want to loose? I think you should get everything working out of the box, as for the drivers, why do you think Dell provides something special that isn't available in 9.04?


The mini 10v trackpad is a bit unique due to the trackpad surface actually covering the left and right buttons.  When I first got my mini 10v I briefly installed the standard ubuntu 9.04 and the trackpad seemed to be way too touchy (holding down the left button while scrolling was also a tad bit insane).  I was wondering if Dell had a special driver or patch or something (remember I am a noob) for the trackpad that I could apply.

How do special hardware patches get applied in ubuntu?  Is there a automatic discovery process of the hardware that gets addressed in the automatic updates?  If not then Is the standard approach to google for the problem and search for a patch/solution to any hardware issues.

... thanks for the kind responses.  I plan on installing the standard 9.04 again this evening via usb and see if I can address my trackpad issue.

Any additional advice is welcome.

---

### Post by snowpine on 2009-08-05
If the Mini 10v is the same as my Mini 9, the trackpad driver is called synaptics and is included in the default Ubuntu install. You can install an application called gsynaptics (from the terminal, 'sudo apt-get install gsynaptics') to tweak the trackpad settings graphically.

---

### Post by chf on 2009-08-05
Hello,

I can also recommend Ubuntu Netbook Remix (UNR) for the mini10v.
I'm using it since a few days and it works very well. However I have the same problem with the trackpad. Maybe the suggestion above can solve the problem.

Best regards

chf

---

### Post by mikewhatever on 2009-08-05
I think you are going way to far troubling yourself with issues you most likely will not have to deal with. There is a bunch of users running Ubuntu on Dell minis 10 and 10v, and no touchpad problems had been reported.
Can anyone confirm mini 10s have synaptics touchpads? I've looked through the hardware list and found no mention.

---

### Post by Dante123 on 2009-08-14
Wife has mini10v with 9.04

Mom has mini10v with Dell's 8.04 version

Wife's touchpad has a slight usability problem where you use the right and left corners same as a mouse buttons.  You go to click the say left button and it moves the cursour slightly.  Seems like the actual button surface is too sensitive.  It is annoying.  Mom's dell with 8.04 does not have this issue.  Hoping someone has a solution.

:confused:

---

### Post by karamu on 2009-08-26
I have installed 9.04 then Karmic alpha 3 on my Mini 10v. I would agree that the touchpad is kinda jumpy but I don't recall it being much better with Dellbuntu 8.04....

I got pissed off with the Dell install of 8.04 and put in Jaunty (regular version, not UNR- the maximus thing did my head in with the Dell version so I didn't want that). It basically worked well- I got Compiz working which I couldn't do with Dellbuntu but I did run into a couple of issues:
[LIST]
[*]Getting Skype to work was unreliable with the audio hardware (even with my headset)
[*]My MP3 player (Toshiba Gigabeat U) wouldn't mount or sunc using Banshee
[/LIST]
So, I installed the alpha 3 of Karmic and everything works fine- the whole experience is slightly buggy- apps do crash at times- but it is a pre-release so I can't complain- come October all will be fine!

---

### Post by Bonji on 2009-08-26
I was trying to use the standard upgrade method through the Software Sources menu.  However, the only option is to check for standard upgrades.  I can not specify that I want to upgrade to a newer version of Ubuntu.  Is this because Dell disabled it?

---

### Post by Bonji on 2009-08-27
> **snowpine said:**
> If the Mini 10v is the same as my Mini 9, the trackpad driver is called synaptics and is included in the default Ubuntu install. You can install an application called gsynaptics (from the terminal, 'sudo apt-get install gsynaptics') to tweak the trackpad settings graphically.

Ok, I'm a noob and need some help.  I installed gsynaptics and when I try to run it i get the following message, "SHMConfig must be set to True in either xorg.conf or xf86Config".  Not sure how do edit those files.

---

### Post by snowpine on 2009-08-27
> **Bonji said:**
> Ok, I'm a noob and need some help.  I installed gsynaptics and when I try to run it i get the following message, "SHMConfig must be set to True in either xorg.conf or xf86Config".  Not sure how do edit those files.

Hi Bonji, I've never seen that error message before, but I will try my best to help you. :)

Let's start with the obvious: Which model of Dell Mini do you have, and which Ubuntu release are you using (Dell 8.04 Hardy Heron, Ubuntu 9.04 Jaunty Jackalope, etc.)?

---

### Post by Tyrathect on 2009-09-21
Here's a guide to get the trackpad working under Jaunty on a 10v

[http://ubuntuforums.org/showthread.php?t=1270382](http://ubuntuforums.org/showthread.php?t=1270382)

---

