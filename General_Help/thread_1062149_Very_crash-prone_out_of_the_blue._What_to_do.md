---
title: "Very crash-prone out of the blue. What to do?"
date: 2009-02-06
forum: General Help
---

### Post by Redsandro on 2009-02-06
All of the sudden, since a month or so, my Linux machine usually chrashes the first time I boot, sometimes also the second time (after immediate reboot) and occasionally it doesn't crash.

It has been working perfectly for a year. I rarely use it myself, but it acts as a file server. I turn it on, it synchronises data, and at the end of the day I turn it off again. Sometimes I play the occasional game (but only games that I installed a long time ago before there were problems) or attach a scanner that is not supported on my working machine (XP64).

I am running Ubuntu 8.04 on a Intel P4 2.4 GHz @ Asus P4C800 mobo with 2GB memory. Video through nVidia geForce FX5200 with proprietary driver.

I only do a manual update about once every 3 months, so updates are probably unrelated, and I don't really think it's hacked/virussed or whatever. Not only because it's linux, but I also got a firewall in my router.

When it crashes, the GUI stops responding and sometimes has a line somewhere over it that's not supposed to be there. At this point I also cannot login through a VNC client.

But **sometimes** I can still use the files over the network (samba) and I can still login with ssh.

I admit I skipped a few fsck's because they always popup in the worst timing, but I forced it with ssh:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102415&stc=1&d=1233952181[/IMG]

And there was no problem found. Now it didn't crash but the computer is just EXTREMELY slow. Ssh is doable but VNC is not - although it does show the screen (after 5 minutes of building it). (update - it crashed soon after that)

I just know how to use linux for setting up file serving and basic stuff I need to do, but I have no idea what to try when things go wrong!

In Windows I'd try [hd tune]("http://www.hdtune.com/") to test performance, watch hd health, and do a deep scan.

What should I do?

---

### Post by LowSky on 2009-02-06
you could always run the Memtest from GRUB or a liveCD, as that will tell you if its motherboard or RAM issue.

check this out too, its alivecd of testing tools
[http://grml.org/](http://grml.org/)

You could also enable SMART monitoring from the BIOS for the hard drives and use a tool like
smartmontools
[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

---

### Post by Redsandro on 2009-02-07
Thanks. I've run Memtest, it passed all tests twice and then I was out of patience. 

I rebooted in order to try smartmontools you mentioned, but it turns out the symptoms have gotten worse. But maybe this helps pinpoint the problem: If I interact with the GUI, a crash will almost certainly happen. If after Gnome loads I immediately switch to TTY, the computer won't crash.

For example, when I try to start Synaptic to see if there is smartmontools, or when I try to update, I never get a chance to finish entering my password.

Lines or black spots appear on screen when crashing, I took a picture of the screen but it shows only one line:
[http://ubuntuforums.org/attachment.php?attachmentid=102534&stc=1&d=1234032973]("http://ubuntuforums.org/attachment.php?attachmentid=102534&stc=1&d=1234032973")

Similar, VNC connection shows noise where Gnome shows black spots on the screen:
[http://ubuntuforums.org/attachment.php?attachmentid=102535&stc=1&d=1234032973]("http://ubuntuforums.org/attachment.php?attachmentid=102535&stc=1&d=1234032973")
BTW - This is probably how VLC interpretes lack of data, for actual on screen is just black.

Can I install all the updates (there are 97 updates) with a command from TTY? Then it won't crash. Also, since updates will probably not fix this, do you have an idea what to try next?

---

### Post by Redsandro on 2009-02-08
Found this somewhere:> sudo apt-get update;sudo apt-get upgrade

But now the GUI won't even load and the screen won't show if I switch to TTY, but the HD light is flashing.

I can log in SSH, but it is so slow (ls takes 5 seconds) that it's probably a bad idea to try an update now.

Oh this is so random. I hate not to know what causes it.

-edit-

When I manage to see the GUI, it often randomly flashes to black for a millisecond.
Maybe my videocard decided to give the gost, even though it has the most lazy life ever?

---

### Post by Redsandro on 2009-02-11
Bump

I tried MemTest for a few hours without problems. Then finally I found myself a LiveCD which runs without problems. So I'd say *something* in the GUI or an autostarted app has become corrupted.

Is there a way to find out what causes this?
Is there a way to reinstall Gnome without losing all config and changes?
Is there maybe a tool that automatically checks if systemfiles are different from what they are supposed to be?

Just a guess:
Gnome is just gone corrupted;
or wine (autostarts) is corrupted;
or Nvidia-Proprietary is corrupted.

Can I edit (disable) autostart apps through TTY?

---

### Post by Redsandro on 2009-02-12
I edited xorg.conf to use **nv** in stead of **nvidia** and it hasn't crashed since. Not I am really confused.

I have been using the proprietary driver for 4 years. I don't think my videocard is broken because nv also has some hardware support.

Please, any suggestions?

---

