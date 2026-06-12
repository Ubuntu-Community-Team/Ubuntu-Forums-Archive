---
title: "Blank screen on boot"
date: 2009-05-03
forum: General Help
---

### Post by SilentFlame on 2009-05-03
Hi, I'm new to Ubuntu and could use some help. 

I recently switched from Windows Vista to Ubuntu 9.04. I'm having an issue on boot where post-splash screen the logon screen does not display. The monitor flickers approx. 3 times and then nothing. No response to keyboard/mouse, my only option is to reboot. 

On a fresh install it works perfectly fine, but once I turn my computer off, this problem occurs, forcing me to re-install. 

I have tried editing the kernel to eliminate ACPI and the splash screen but to no avail.

Booting in recovery mode and applying the graphical fix, the hard disk check, etc does nothing to fix it. 

I'm running an ATI Mobility Radeon HD 3650
2 GB RAM

I don't know what type of specs you guys require for fixing this type of issue, but if I had to guess I'd say it has something to do with my video card. 

Any help would be appreciated. :)

---

### Post by davace on 2009-05-24
I am having this exact same problem on my machine, down to the LCD screen's backlight flashing 3 times before the machine crashes completely (flashing about 1 sec on, then one sec off...).   I have an Ubuntu 9.4 install and my video card is an onboard one using the Q965 chipset.

Directly after installing everything was fine.  The problem first occured after a rather hefty Synaptic install session so obviously something that I installed is causing the conflict.  I've had past linux experience, but none with ubuntu and I'm having trouble finding locating things that I know should be there somewhere.

My situation is complicated by the fact that my internet access is via wireless broadband connected directly to this computer and I can come up with no way to connnect it without the use of the graphical nm-applet which of course I cannot run.  This makes it impossible to remove and re-install any package that may remotely be the culprit.

So, if anyone can help me with one of these problems I would be very greatful:

(a) how can I connect to my wireless broadband after booting in rescue (root-only) mode?

(b) how can I figure out exactly what is going wrong - I presume it is X failing to initialise, but having searched both the web, and my hard-drive can see no signs of errors in any log-files (at least not those that I can find).

(c) I (think) the attached file contains all the packages that I have installed recently - this is a grepped/sedded version of /var/log/apt/term.log file.  I presume that one of these is probably the culprit, but their names mean nothing to me.  I have vague memories of installing a package that promised to look after all my ATI device drivers but can not for the life of me find it.  Searching for ATI through all the online package lists I can find did not help.  I cannot however, find the package files that I'm sure should be on my computer somewhere...

Please help, I am nearly running out of hairs to pull.

Thanks,

David

---

### Post by utnubuuser on 2009-05-24
Out of curiosity, is this strictly a 9.04 problem, or something that carries over from version to version?

re- network in terminal:[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

And for network (wireless):> ifup wlan0 or ifconfig wlan0 upor maybe > ifup wlan1 or ifconfig wlan1 up
and for ethernet> ifup eth0 or ifconfig eth0 up

etc, etc.  all commands preceded by **sudo**
> sudo ifconfig -awill give a list of aavailable devices

---

### Post by davace on 2009-05-24
I'm not sure if its version related - this is the first time I have installed ubuntu so I cannot tell.

But, I have managed to fix it - YAY!!!  (must be time to sleep for the first time in 36 hours :)

As it turns out, I was right - /var/log/apt/term.log IS a valid way to check recent apt-get activity.

The only two changes that I made are shown in the log excerpt below.  I firstly removed envy - although this had never installed properly, I had only ever tried to install it after my problems began.

Then I had a wild guess and removed the package "xorg-driver-fglrx".  After rebooting, into normal mode (I had done this from safe/root only mode) everything loaded as it should.  Unfortunately I am still none the wiser as to what went wrong in the first place.

Thankyou for your help it is most appreciated.

Hopefully, this may help out SilentFlame too... I'll cross my fingers and leave it to you to mark the thread solved.

Cheers,

David



PS.  Here is the tail of :/var/log/apt/term.log"

Log started: 2009-05-25  07:13:32
(Reading database ... 166895 files and directories currently installed.)
Removing envy ...
Log ended: 2009-05-25  07:13:46

Log started: 2009-05-25  07:14:11
(Reading database ... 166541 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing xorg-driver-fglrx ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2009-05-25  07:14:14

---

