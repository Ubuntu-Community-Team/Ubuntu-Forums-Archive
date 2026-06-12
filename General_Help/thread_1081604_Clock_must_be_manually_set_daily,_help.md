---
title: "Clock must be manually set daily, help?"
date: 2009-02-26
forum: General Help
---

### Post by puscifer919 on 2009-02-26
Hey everyone, can someone please tell me why I keep having to manually set the clock time in the upper Panel in Ubuntu? Everyday at some point while I'm using the system, the clock will just stop at a certain time and refuse to change until I right-click it, select Adjust Date & Time, click Set System Time, and then enter my password. It's very annoying and has almost caused me to be late to work multiple times.

I also run Windows XP and Windows 7 Beta on this machine and I do not have any issues with those (in case anyone was thinking CMOS battery or something).

Sorry if this was answered somewhere else on the forums, I didn't find anything helpful through searching.

Thanks in advance!

---

### Post by Xiong Chiamiov on 2009-02-28
You can try [enabling NTP](https://help.ubuntu.com/community/UbuntuTime#Time%20Synchronization%20using%20NTP), if it's not already.

---

### Post by 440corbon on 2009-02-28
I have no solution for you, but I had a similar problem. I had a dual boot system using sepperate hard drives and my Windows clock kept changing. I gave up on Ubuntu for a while. I'm just running a wubi install right now.

---

### Post by fifth on 2009-02-28
Probably too obvious a reply, but do you have have your time zone set correctly?

[edit] Nevermind, didnt read your post fully, I assume the time initially shows up correctly?

---

### Post by steveneddy on 2009-02-28
Have you recently upgraded?

Are you running 64 or 32 bit?

What version of Ubuntu are you running?

From some old notes:

> ## setting time


#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

---

### Post by spcwingo on 2009-02-28
Sometimes a failing CMOS battery can do this too.

---

### Post by puscifer919 on 2009-03-03
Thanks for all the replies. I tried everything posted and nothing seemed to change the behavior.

What I did do (simply enough) was add a "Location" in the Locations tab of the clock preferences window. There was none set before so that may have been the problem. It hasn't been an issue since, but isn't this supposed to be set when you first install Ubuntu?

Oh well, I'll post back if the issue occurs again. Otherwise, thanks for the suggestions!

---

### Post by puscifer919 on 2009-03-04
My solution fails this morning.

I am trying the NTP solution again, as it seems to make the most sense seeing as how I'm always connected to the internet.

One question, how do I make sure it runs at startup? Is there a command I can add to the Session Manager's Startup Programs tab, or will it happen automatically now that NTP is installed?

---

### Post by philinux on 2009-03-04
System>admin>time and date.

Change the setting from manual to synch with servers.

---

### Post by wildman4god on 2009-03-04
> **spcwingo said:**
> Sometimes a failing CMOS battery can do this too.

I second this as the most likely cause of this problem.

---

### Post by heindsight on 2009-03-04
> **440corbon said:**
> I have no solution for you, but I had a similar problem. I had a dual boot system using sepperate hard drives and my Windows clock kept changing. I gave up on Ubuntu for a while. I'm just running a wubi install right now.

A bit off topic, but I just thought I'd mention that that particular problem probably came about because windows and ubuntu had different ideas about the timezone of your hardware clock. I'm not sure if it's still the case, but I believe windows used to simply assume that the hardware clock is set to local time, while linux usually assumes (unless you tell it otherwise) that the hardware clock is set to UTC time.

---

### Post by puscifer919 on 2009-03-05
> **philinux said:**
> System>admin>time and date.

Change the setting from manual to synch with servers.
It is currently set that way, unfortunately.

> **wildman4god said:**
> I second this as the most likely cause of this problem.
I don't think it is. It doesn't behave this way in Windows, it happens even after the machine has been running for days, and it is a brand new machine. The time is also initially correct even after leaving the system off and unplugged overnight.

> **heindsight said:**
> A bit off topic, but I just thought I'd mention that that particular problem probably came about because windows and ubuntu had different ideas about the timezone of your hardware clock. I'm not sure if it's still the case, but I believe windows used to simply assume that the hardware clock is set to local time, while linux usually assumes (unless you tell it otherwise) that the hardware clock is set to UTC time.
I don't know if it has anything to do with a problem between Ubuntu and Windows or not. What I do know is that the clock is RIGHT when I login to Ubuntu, always, and then after a few hours it just stops at any given time and doesn't change. If I right-click it and select Adjust Date & Time, the window that pops up shows the correct time, ticking away, while the panel clock stays put until I click Set System Time and put in my password.

---

### Post by heindsight on 2009-03-06
> **puscifer919 said:**
> I don't know if it has anything to do with a problem between Ubuntu and Windows or not. What I do know is that the clock is RIGHT when I login to Ubuntu, always, and then after a few hours it just stops at any given time and doesn't change. If I right-click it and select Adjust Date & Time, the window that pops up shows the correct time, ticking away, while the panel clock stays put until I click Set System Time and put in my password.

Sorry, yes. I don't believe the problem you're having has anything to do with what I posted before. I was merely pointing out a possible reason for the problem 440corbon described (where windows always has the wrong time).

Regarding your problem, I'm afraid I've no idea what could be the cause, but it sounds to me as if there's a glitch in the panel clock applet. Especially since the correct time is shown in the Adjust Date & Time window. Just to confirm, next time it stops, try running:
```
date
```
in a terminal and see if that gives correct output.

What happens if, instead of setting the time, you just remove the applet from the panel and then add it again?

By the way, what version of Ubuntu did you say you're using?

---

### Post by puscifer919 on 2009-03-06
> **heindsight said:**
> By the way, what version of Ubuntu did you say you're using?
I am using 8.10. I haven't had a chance to use the date command yet, but I highly suspect it would display the correct time.

I should also note something I just noticed. Beside my clock in the panel is my username with the icon beside it which correlates to my status in Pidgin. I noticed the clock was locked up again, so I logged into Pidgen and the status icon beside my username did not change. I then manually adjusted the time using the Set System Time button in the Adjust Date & Time window, and along with the clock updating, the status icon also switched to the green circle (Available status).

Could this be an issue with the panel not updating or refreshing? I'm not really familiar with how processes are handled in Ubuntu, but could it be that the process that controls the panel goes into a sleep or standby status of some sort?

---

### Post by puscifer919 on 2009-03-10
It's sitting here stuck, as I'm typing this. It's stuck right at the time I sat down at the computer (exactly 5 minutes ago) and I'll I've done is open Firefox and Pidgin.

Screenshot:
[img]http://cubeupload.com/files/1fb400panel.png[/img]

I'm suspecting one of two things. Either;

a) Pidgin causes the panel to hang while it is trying to update the status icon beside my username, or

b) Opening Firefox and Pidgen rapid fire caused some sort of lockup. I do tend to click things quickly, but I can't really imagine that would make a difference.


Note that the Application, Places, and System menus work fine, along with the shortcuts to my programs. Clicking on the "empty" gap in the panel produces whatever effect the icon that *should* be there would do. For instance, I just clicked somewhere near the middle and my buddy list disappeared.

Note: Closing Pidgin caused the time to jump to the correct time. This may just be because the panel was forced to update, because it had to remove the Pidgin icon from the running programs section and then resize itself. Not sure, but I hope this gives someone an idea of what's going on. I just opened Pidgin again and it didn't cause any issues.


EDIT: I just reproduced the issue using the b) scenario above. That is, I closed both programs completely. Then clicked the Firefox icon, immediately followed by the Pidgin icon. Pidgin began loading before the Firefox window even appeared, and the clock and status icon are both as they were 3 minutes ago. I suppose this isn't that big an issue anymore, maybe just a glitch with either the panel itself, or the status icon being integrated into the end of the panel. :-k

---

### Post by lotech on 2009-03-16
I am using Ubuntu Remix on USB flash boot but I think it is the same as normal hard disk boot. My time zone does not save, I've to change it every time reboot, and I've NTP installed but the time zone field is blank when boot up, I've to manually change it to correct the time, other changes saved back to USB flash no problem, any idea ?

---

