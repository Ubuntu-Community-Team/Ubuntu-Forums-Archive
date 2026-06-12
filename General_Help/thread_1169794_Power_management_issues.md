---
title: "Power management issues"
date: 2009-05-25
forum: General Help
---

### Post by nixIT on 2009-05-25
Hello all,

Recently upgraded from 8.10 32-bit to 9.04 32-bit via a fresh install.  In 8.10, I would set the power management to turn off monitor in 15 minutes.  After 15 minutes of idle time, my monitor would power off/go to sleep, and the green power light would turn to amber.

After the fresh install of 9.04, my monitor will turn black, but the green power light will not turn amber, and the monitor never really "goes to sleep".

Is this a bug?  Any ideas how I can fix it if it is not a bug?

--nixIT

---

### Post by dnairb on 2009-05-25
Probably screensaver setting. IIRC the default screensaver is a blank screen, set to start after 15 minutes idle time.
Try changing the settings: System -> Preferences -> Screensaver

---

### Post by nixIT on 2009-05-25
I don't think you understand, my monitor goes blank, like a blank screen saver, but it does not turn off(power light turn to amber) after my 15 minutes like it should be doing.

My monitor would turn off with this setting in 8.10, but not in 9.04.

Does anyone else have this issue?  if not, where should I look to fix?

--nixIT

---

### Post by cottfcfan on 2009-05-26
Ive just realised ive got the same problem, but i dont know what the answer is.

---

### Post by nixIT on 2009-05-26
At least someone acknowledges that there is a problem.  Whew, i thought I was going bonkers.  :)

Has anyone else run into this issue?  is it a bug?  Is monitor power management controlled via some other mechanism?  

I would hate to have to reinstall 8.10.

--nixIT

---

### Post by nixIT on 2009-05-26
> **cottfcfan said:**
> Ive just realised ive got the same problem, but i dont know what the answer is.

At 4:20 today something occurred to me.  What video drivers are you using?  I am, or was, using the ATI drivers that were installed via Envy.  I noticed that the ATI Control Center would load either.  I just un-installed those drivers and enabled the drivers under System/Hardware Drivers/.

I can now load the ATI Control Center. Lets  see if the monitor will now go to sleep.  Will report back in about 1 hour.

--nixIT

---

### Post by nixIT on 2009-05-27
I uninstalled the drivers via envy, installed the drivers though Hardware drivers, and no luck, I get the same behavior, power management does not turn my monitor off.  However, with those drivers, my system appears to come to a crawl.  

Unfortunately, I can't use a system like this.  The system operated better with the drivers installed via Envy, but 8.10 ran on my system much better.

I am in the process of going back to 8.10.  :(

--nixIT

---

### Post by nixIT on 2009-05-28
for all those following this post, I downloaded and installed a fresh copy of Ubuntu 9.04 64-bit.  Had bad luck with the first install of 64-bit (computer running sluggish).

After a fresh install and updates, the power management in the 64-bit version works correctly, after 11 minutes my monitor did turn off.

I will mention that I have not installed the ATI drivers for my video card, I did not have time, though I will be installing those today.

Any recommendations on how to install the latest drivers properly?  I used to install all my video drivers by using envyng.

--nixIT

---

### Post by nixIT on 2009-05-30
I'll be a monkey's uncle.  

With a fresh install of Ubuntu 9.04 64-bit, and updates, the power management worked as expected, and my monitor went to sleep.  I installed the ATI drivers via the Restricted Device Manager (The Ubuntu Way), and now my monitor won't go to sleep.

Any ideas why?  or how to fix?  At least I and maybe we know what was causing the monitor to not sleep.

--nixIT.

---

### Post by nixIT on 2009-06-10
I figured out what was wrong.  Don't ask me how or why, but I manually installed the ATI drivers via this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

Step 5 "[Installing the drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually")"

And all my power management issues went away.

So, installing via the restricted hardware drivers in Ubuntu did not work, installing via Envy did not work, but manually installing worked like a charm.

So, if anyone is following this thread, the above worked for me.

--nixIT

---

### Post by hilltop on 2009-06-10
I have a similar but not exactly the same situation.  I recently did a clean install of jaunty 9.04 64-bit version.  Went fine.  Then, because I have an nVidia Quadro FX580 adapter, I installed the nvidia proprietary drivers version 180.44 from the Restricted Hardware Drivers (now called Hardware Drivers) from the System/Administration menu -- the Ubuntu way, as you said it.  I have the same problem of no power management for the display.  The screen simply goes blank but remains on, consuming power.

I can't use the ATI manual installation instructions that you reference above, for obvious reasons, but I do know that there are instructions for manually installing the nvidia drivers as well.  I just opted not to use them the first time as I am a relative linux noob and wanted to follow a safer route.  If any video driver installation experts out there can give me some reassurance and a pointer to the 'right' set of instructions (I've seen several conflicting sets), I would be obliged.

---

### Post by cottfcfan on 2009-06-23
I installed the proprietary ATI driver from there web site.
Now my screensaver & power off work fine.

---

