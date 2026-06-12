---
title: "Suspend/Resume on m1330 works on Hardy (8.04)"
date: 2008-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by akniss on 2008-05-04
After some tweaking, I've got my m1330 with Intel X3100 graphics suspending and resuming without failure. In order to get it to this point, I had to make some changes to /etc/default/acpi-support.  I have posted the file in its entirety so that others might try the settings on their machines.  

EDIT: If you have an Nvidia card instead of the Intel X3100, some users have found that adding nvidia to the modules whitelist section has helped get their machine suspending/resuming consistently.

```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
# ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="uvcvideo"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# If you have an Nvidia graphics card, you may want to comment the previous
# line and un comment the following line
# MODULES_WHITELIST="nvidia"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
# LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12
```

---

### Post by pormogo on 2008-05-04
***MODULES="uvcvideo"***

Rad, while it was working fine before this greatly improved my resume time!

---

### Post by atlas95 on 2008-05-04
Good ! If you have other improvements like laptop-mode,spindown time  etc I take them :)

---

### Post by addiebk on 2008-05-05
Any chance helping a complete n00b figure out how to do that?

---

### Post by atlas95 on 2008-05-05
Do:

sudo gedit /etc/default/acpi-support in a terminal, then copy/paste the content of first post :)

---

### Post by zmunson on 2008-05-07
akniss, thanks for the code!  It mostly worked for me, a relative newbie.  Resume on my M1330 with 8.04 still presents me with a completely white screen, however.  I have to input my password blind before I get a proper desktop.  This is a problem, as the marital unit is not going to be happy with no password window/prompt.  

Has anyone else seen this?  Any way to clean it up?

Thanks,
Z

---

### Post by LibertyShadow on 2008-05-07
Both suspend and hibernate work out of the box (most of the time) on my nvidia XPS M1330 with 64-bit Hardy!

However, on resume I get the white screen sometimes.  It seems to be a known bug. [https://bugs.launchpad.net/dell/+bug/160264]("https://bugs.launchpad.net/dell/+bug/160264")

---

### Post by thorcik on 2008-05-08
on 32-bit Ubuntu it works fine as well. at last I can make my system hibernate instead of powering it off :o)

---

### Post by jberger on 2008-05-08
When returning from suspend or hibernate my screen is blank and the only thing to do is to turn off the computer. I run Hardy on XPS M1330 with nVidia.

---

### Post by HanZo on 2008-05-09
Does not really seem to affect anything. Still get those white screens of doom... and one time I even had a complete lockup when resuming... :(
I run hardy on an XPS 1330 with nvidia card.

---

### Post by cespinal on 2008-05-09
YESSSS IT WORKED!!!

I have got an hp dv9000 with an nvidia card with restricted drivers... 
I just made a minor tweak to the file, leaving it as follows:

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
# ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULsudo gedit /etc/default/acpi-support in a terminalES_WHITELIST
MODULES="uvcvideo"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="nvidia"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
# LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12

---

### Post by unlotto on 2008-05-10
Tested it a few times and the settings work for me on my m1330. Suspend to disk always worked but suspend to ram did not. It does now.

---

### Post by PhrygianCat on 2008-05-10
> **jberger said:**
> When returning from suspend or hibernate my screen is blank and the only thing to do is to turn off the computer. I run Hardy on XPS M1330 with nVidia.
I got that too every once in a while, but I found out that when I go ahead type my password & hit enter, it works just fine. At first I kept on restarting gdm, but one day I decided to just try it as if I see the dialog to enter the password and to my surprise it worked.

---

### Post by PeeZz on 2008-05-11
All of this doesn't work for me.

I have a Sony Vaio VGN-FZ29VN with Hardy 64 bit installed.

When I try to hibernate/suspend, my screens dims, shuts down 1 second, goes on and shows just one blinking white cursor ( like this " _ ") on a black screen.

Anyone? :)

---

### Post by PhrygianCat on 2008-05-11
> **PeeZz said:**
> All of this doesn't work for me.

I have a Sony Vaio VGN-FZ29VN with Hardy 64 bit installed.

When I try to hibernate/suspend, my screens dims, shuts down 1 second, goes on and shows just shows one blinking white cursor ( like this " _ ") on a black screen.

Anyone? :)
Then what happen? Your computer hung? Is it problem with gdm? Can you try logging in in TTY1?

---

### Post by PeeZz on 2008-05-12
> **PhrygianCat said:**
> Then what happen? Your computer hung? Is it problem with gdm? Can you try logging in in TTY1?

Nothing happens then.. The white cursor keeps on blinking (I don't know the right word in English for that) in the upper left corner of my screen. It's the same for suspend and hibernate.

How can I analyze the problem? How can I know it's gdm?
And what is TTY1? :)

-- HDV

---

### Post by akniss on 2008-05-12
> **PeeZz said:**
> Nothing happens then.. The white cursor keeps on blinking (I don't know the right word in English for that) in the upper left corner of my screen. It's the same for suspend and hibernate.

How can I analyze the problem? How can I know it's gdm?
And what is TTY1? :)

-- HDV

A few questions:
Which video card do you have?  
Do you have the Dell XPS m1330? 
Did you do a clean install of Hardy, or did you upgrade from Gutsy?

---

### Post by PeeZz on 2008-05-12
> **akniss said:**
> A few questions:
Which video card do you have?  
Do you have the Dell XPS m1330? 
Did you do a clean install of Hardy, or did you upgrade from Gutsy?

My video card: Intel GMA X3100
My laptop: Sony Vaio VGN-FZ29VN (maybe I shouldn't post here?)

And I did a clean install. I'm using the 64 bit edition.

Maybe this helps..

-- HDV

---

### Post by PhrygianCat on 2008-05-12
> **PeeZz said:**
> Nothing happens then.. The white cursor keeps on blinking (I don't know the right word in English for that) in the upper left corner of my screen. It's the same for suspend and hibernate.

How can I analyze the problem? How can I know it's gdm?
And what is TTY1? :)

-- HDV
In Ubuntu TTY1 - TTY6 are the virtual consoles. You can get to TTY1 by doing CTRL+ALT+F1. CTRL+ALT+F7 will get you back to x, the 'windows' interface.

Try narrowing down your problem by going to TTY1 and login as yourself. If you can login, type this command: sudo /etc/init.d/gdm restart

Let us know the result.

---

### Post by zmunson on 2008-05-12
As a note to other's trying to get suspend/resume working on their M1330s: The only difference between the /etc/default/acpi-support file posted by akniss to start this thread and the one posted by cespinal is the MODULES_WHITELIST="nvidia" line (akniss has this line set to null).

As I previously posted, the akniss file worked for me except that I get a completely white screen on resume until I (blindly) enter my password.  I tried the cespinal version and it didn't help.  And for some reason, the cespinal version caused me to lose all my sound.  Reverting back to the akniss version restored my sound.

I'm on a M1330 with the Nividia 8400 card, BTW.

-Z

---

### Post by ethanay on 2008-05-12
Changing acpi values no longer works for me, since pm-utils (/usr/lib/pm-utils/ and /etc/pm/) are handling sleep and power state for me.

see [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/147757/comments/15") at launchpad for a pm-utils workaround.

---

### Post by PeeZz on 2008-05-12
> **PhrygianCat said:**
> In Ubuntu TTY1 - TTY6 are the virtual consoles. You can get to TTY1 by doing CTRL+ALT+F1. CTRL+ALT+F7 will get you back to x, the 'windows' interface.

Try narrowing down your problem by going to TTY1 and login as yourself. If you can login, type this command: sudo /etc/init.d/gdm restart

Let us know the result.

Well, I tried it out. But nothing happens when I do CTRL+ALT+F1. I even tried F2 - ... - F7.

If you don't know an answer, I'll go on without suspend/hibernate :).

-- PeeZz

---

### Post by akniss on 2008-05-13
> **PeeZz said:**
> Well, I tried it out. But nothing happens when I do CTRL+ALT+F1. I even tried F2 - ... - F7.

If you don't know an answer, I'll go on without suspend/hibernate :).

-- PeeZz

Perhaps it has something to do with 64-bit.  I'm running 32bit.  Can anyone comfirm whether suspend works on 64 bit with this configuration?  Otherwise it might be related to some other hardware configuration difference between your Sony and the Dells.

---

### Post by rockhopper on 2008-05-21
Does this method guarantee that you don't lose one of your CPU cores?

Suspend (working out of the box) takes out one of my cores; so that I can no longer control it using the gnome-applet.

---

### Post by akniss on 2008-05-21
> **rockhopper said:**
> Does this method guarantee that you don't lose one of your CPU cores?

Suspend (working out of the box) takes out one of my cores; so that I can no longer control it using the gnome-applet.

This doesn't really 'guarantee' anything.  I'm using 32-bit, and I do not 'lose' either of my cores.  However, since I'm running 32-bit, I can't really control them independently anyway.  I don't see any settings in the acpi file posted that would fix this problem for you, but its worth a try.

---

### Post by zmunson on 2008-06-04
> **ethanay said:**
> Changing acpi values no longer works for me, since pm-utils (/usr/lib/pm-utils/ and /etc/pm/) are handling sleep and power state for me.

see [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/147757/comments/15") at launchpad for a pm-utils workaround.

Ugh!  My suspend no longer works.  The acpi change *did* work for me for awhile.  But it stopped working several days ago.  I have no idea why (one of the security updates?).  Now my M1330 won't go into suspend the *second* time I attempt it after a reboot (interestingly, suspend does work once after a reboot; only subsequent suspends fail).  The machine never suspends.  It simply stays on with a blinking cursor in the upper left of the screen.  I have to manually power down.  Help!

Ethanay: Where do you put the workaround mentioned by TJ in his comment on bug 147757?  Do you just add the line to /usr/lib/pm-utils/defaults?  (The line: echo "SUSPEND_MODULES=\"uvcvideo\"" >/etc/pm/config.d/unload_modules chmod +x /etc/pm/config.d/unload_modules)

-Z

---

### Post by Paul S on 2008-06-04
> **zmunson said:**
> My suspend no longer works.

This seems to be the nature of suspend / hibernate .. that it works for a while, but then stops for no known reason.

> **zmunson said:**
> 
Ethanay: Where do you put the workaround mentioned by TJ in his comment on bug 147757?  Do you just add the line to /usr/lib/pm-utils/defaults?  (The line: echo "SUSPEND_MODULES=\"uvcvideo\"" >/etc/pm/config.d/unload_modules chmod +x /etc/pm/config.d/unload_modules)

-Z

Hardy is using pm-utils for suspend and hibernate.  According to pm-utils man pages, it's possible to put custom changes in files in /etc/pm/ directory.  What the command above does is create a file named unload_modules in the /etc/pm/config.d directory and give it the contents of SUSPEND_MODULES="uvcvideo" and then making it executable with chmod.

I don't have a uvcvideo, but do have occasional loss of usb after resuming, so have added "usbhid uhci-hcd" into my custom modules list.

How do you know what modules are failing ... you might see it on /var/log/messages after losing some system on resume.

Still, resume is what it is .. it works (sometimes) for some laptops, and less well for others.

But, devs are working on making it better.  I think hardy is better than gutsy.

In my case, whenever I've run windows, I've also had some suspend / hibernate resume failures, so I have less expectation that it can be done flawlessly.

regards,

---

### Post by ethanay on 2008-06-04
yes, as Paul S mentioned, you can simply run the commmand (open a terminal, type or copy/paste :) 

but I found it kind of sloppy to do that when there is /usr/lib/pm-utils/defaults

which contains (first line, i think) the same command:  SUSPEND_MODULES="" just put uvcvideo in between the quotes

[http://en.opensuse.org/Pm-utils](http://en.opensuse.org/Pm-utils)
but be aware that an upgrade of the pm-utils package will reset it.  putting it into /etc/pm/config.d will over-ride the "defaults" file and so is more "permanent."

However i am still working on some errors that cause a "failure" notice even though everything appears to work ok, and causes a strange behavior right before hibernate:  after all memory is dumped to hard drive, the hard drive shuts down, then turns on again really quickly to record another error about USB not wanting to turn off.

I think it is related to [bug 229932]("https://bugs.launchpad.net/ubuntu/+bug/229932")

---

### Post by atlas95 on 2008-06-05
On my XPS m1330, with uvcvide in pm config I have yet the error message :/
There is a solution with maybe a svn module?

---

### Post by betatester88 on 2008-06-17
Just got my system suspend to RAM working after days of trying.  Combination of the new kernel and the quirk settings make it work.

System info: 
Abit IP35-E
Nvidia 8500GT driver 169.12
Kernel: 2.6.24-19-generic (won't work with any older versions)

NOTE: no "acpi-support" or "apmd" package installed
ONlY with "acpi" and "acpid" installed.  No acpi-support file in /etc/default.  The only changes is the following.

create a file at /usr/share/hal/fdi/information/10freedesktop name "20-video-quirk-pm-nvidia.fdi" or whatever you like.  The follow quirk will match if the driver is "nvidia"

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<match key="info.linux.driver" string="nvidia">
<merge key="power_management.quirk.s3_mode" type="bool">true</merge>
<merge key="power_management.quirk.s3_bios" type="bool">false</merge>
<merge key="power_management.quirk.save_pci" type="bool">false</merge>
<merge key="power_management.quirk.vbemode_restore" type="bool">false</merge>
</match>
</device>
</deviceinfo>

---

### Post by karlatsaic on 2008-08-18
THANK YOU - just what I needed

---

### Post by jmjohn on 2008-09-04
Hello all,

I have a Dell XPS M1330 also, and I've been tweaking the suspend settings.

I didn't have any video, or my video was grainy and ugly after wakeup from suspend, until I whitelisted the module.
[INDENT]
$ gksu gedit /etc/default/acpi-support

# Add modules to this list to leave them in the kernel over suspend/resume
#  uvcvideo added by jeremy
MODULES_WHITELIST="uvcvideo"[/INDENT]


Also, while I'm on the subject, my usb controller wasn't waking up, so I had no power to the usb, including my mouse and keyboard.  So I followed instructions from I forget where, but I'll just post the settings here:

[INDENT]# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
# ohci_hcd ehci_hc  added by Jeremy
MODULES="ohci_hcd ehci_hcd"[/INDENT]

---

### Post by Denny Johnson on 2008-09-05
x

---

### Post by hlainchb on 2008-09-07
I haven't tried the mods suggested here yet (I am about to) but I wanted to throw in that when I get the "white screen of death" I just hit ALT-F7 to take me to the main Gui enabled session and all is well.
Cheers,
H

---

### Post by lcraae on 2008-09-28
Hey guys,

recently received my new M1330 which I've set up with Hardy. Unfortunately suspend, which I'm quite dependent on, only works maybe 2 out of 3 times. Much tweaking of acpi support and pm-utils, according to the tips in this thread, hasn't changed the situation much.

The machine usually suspends, but only leaves me with a blank screen after wake-up. Swapping TTY or entering my password doesn't change that and I have to reboot.

It's not clear to me from the logs exactly what fails (however nothing seems to be logged from the failed wake-ups). Should I post this as an official bug somewhere along with the logs?

I'm sorry, but it's totally unacceptable that it's this error prone.

---

### Post by psychosibes on 2009-10-25
Its been a while since the last post of this thread, but I have had same problem with my 2 year old XPS M1330, which I now dual boot Hardy Heron with Windows Vista Business.
Using the POWER MANAGEMENT settings in the SYSTEMS menu, SUSPEND did not work reliably, but using the tweak from the first posting, it seems to work every time now so long as I suspend using the 'off' button in the panel :). If i just close the lid on the laptop, which should activate suspend, i lose wi-fi on resume and the buttons become unresponsive :confused:. Any ideas?

While i get a say, I have been using Ubuntu since buying a Dell mini 9 a few months ago for my wife. I am IMPRESSED, but I could not have set up my XPS without the help of everyone on this forum. You're all invaluable. Thanks. Anyway, I have now bought a mini 10 with 8.04 for my mum as well !:) BYE BYE WINDOWS !!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by beezdiego on 2009-10-31
I just installed 9.04 on a Dell Inspiron laptop and it doesn't even try to suspend when I close it.  I set it to do so using the GUI controls in the preferences, but I am wondering if the fix above will work since my problem isn't failure to suspend or come out of suspension, it seems to be an issue of recognizing that the laptop has even been closed in the first place.

---

