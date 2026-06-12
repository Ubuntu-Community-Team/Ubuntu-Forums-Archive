---
title: "Monitor/Display resolution change causes break in 11.10"
date: 2012-03-06
forum: Desktop Environments
---

### Post by NamiJason on 2012-03-06
I recently updated to 11.10 and everything has been going great.  The exception has been the monitor display doesn't fill the entire screen and so when I tried to change the resolution as a test using System Settings > Displays I lost the ability to interface. 

The mouse looks fine and covers the entire screen, but I have no ability to reset the display.  I've tried the following based on other searches which haven't worked.

1.  Deleted monitors.xml in the .config folder
2. xrandr --output DFP1 --mode 1920x1080

Neither of those helped.

Right now I have a pretty decent sized paper weight.  Thanks in advance for the help.

---

### Post by NamiJason on 2012-03-07
Also, it wasn't clear from my previous post, but since I can't do anything on the desktop this needs to be fixed through the recovery console.

---

### Post by NamiJason on 2012-03-07
Ok.  So now I tried the post here: 

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) 

And the result is that after reboot, the purple screen pops up as Ubuntu is loading, but then video disappears completely.

At this point I'm headed to a CD or USB stick to boot.

---

### Post by Grenage on 2012-03-07
Greetings,

Did you install the proprietary driver (from 'additional drivers'), or are you using the default open driver?  While I'm not really sure why it's happening, we can try a config file, which may or may not work.

Could you post the output of:

```
lspci | grep VGA
```

Along with the make and model of your monitor.

---

### Post by NamiJason on 2012-03-07
I would love to do that.  I just downloaded the latest USB/CD install download from ubuntu.com.  And am going to try and get to a terminal prompt, but right now I get zero output to my monitor when ubuntu boots up.  It gets the purple screen as if it is about to ask you to login, but then the screen goes black.

Bad news is I am out of the country tomorrow for a week and a half and "the brick" is my desktop here at the house, so this might go dormant for a week if I don't get to it in the midst of packing.

Sorry for the drama, this has been an exciting week to say the least.

---

### Post by Grenage on 2012-03-07
So the CD doesn't boot correctly either?

I'll stay subscribed to the thread, so I notice when you get back and reply. :)

---

### Post by NamiJason on 2012-03-07
I am running off of the CD now.  Its working fine and the monitor is also displaying across the full monitor display which wasn't working before.  

I can get to / on the original system as well.   The drive automounted.

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]

---

### Post by NamiJason on 2012-03-07
Working at the moment...  Not sure if this is a temporary fix and I need to do something else.  

I replaced the /etc/X11/xorg.conf file with the xorg.conf.original that was in the directory and poof.  

The monitor is a Dell ST2410.

---

### Post by Grenage on 2012-03-08
> **NamiJason said:**
> Working at the moment...  Not sure if this is a temporary fix and I need to do something else.  

I replaced the /etc/X11/xorg.conf file with the xorg.conf.original that was in the directory and poof.  

The monitor is a Dell ST2410.

The open driver is generally used by default, so if you were using the proprietary driver before, that could explain the difference.  If it's working now, it's probably worth leaving it as it is; should that change, post back and I'll give you a config file to try out. :)

---

