---
title: "Booting in normal mode, KDE initialization hangs - how do I trace it?"
date: 2005-04-04
forum: Desktop Environments
---

### Post by migrant on 2005-04-04
Hello

At first, I thought that the problems below were caused by not having the 'ac' and 'battery' modules running on my laptop. I am not sure why they weren't added to my /etc/modules file during the Kubuntu install. 

I put those in /etc/modules/ and then I was finally able to boot normally, and I was very glad because I thought I had solved my problems -- until I did apt-get update and upgrade a couple days later. Suddenly, I am back to square one. My 'fix' was still there but my symptom is back.

It is unfortunate that I have never been able to get any response to this -- I see that folks are reading, but I am the only one replying to my messages.

I realized that I might have some configuration here and there to make Ubuntu work -- its just that I thought "community" meant that other more skilled people could help me a little bit if I ran into what to me are major problems using the OS.

As it is, it isn't a question of not wanting to run Ubuntu - it's impossible for me with no means of getting any advice.

Good luck with Ubuntu, guys -- I'm going to switch over to Gentoo with the hope that, if I don't have any support, at least I can learn more about how to fix my problems myself as I go through the lower level installation procedure.

Here is the original information that I provided (I hope it is helpful to someone with a similar problem):

---------------------------------------------------------------------------------------------------------------------------
Since installing Hoary/Kubuntu into my laptop I am only able to boot using Recovery mode, the second GRUB option. I have updated to the latest Kernel (2.6.10.5-686) and have updated all of my packages using Synaptic. 

If I try to use the normal boot, I make it to the log-in screen, log in, and then get the KDE screen where it says 'Initializing peripherals..."  That's where it seems to freeze up. I Ctrl-Alt F1 to a TTY and I see that it completed powernowd initialization, then Samba daemon initialization '[ok]. 

That is the point where it freezes. Sometimes it also says 
/usr/bin/on_ac_power: line 25: 7910 segmentation fault

I looked at /usr/bin/on_ac_power. I don't know what might be going wrong there. It seems to be looking for some directories and files and indicating whether the machine is on ac power or not, but the directories and files it is looking for were not there when I checked, so it looks like it would just pass through and return FF. Line 25 shouldn't even be running in that case. Maybe the directories are there just before the crash. It is a laptop and is on ac power. Even if that is true and this is where the crash happens, I don't know for sure what that implies or what to do next.

A side note is that I am unable to shut down normally when this happens. 

After rebooting and getting a command line prompt in Recovery mode, I've been entering 'kdm' to get running. At that point KDE comes up basically working, including making it through the 'Initializing peripherals' part. 

Unfortunately, doing it that way means many things are not getting initialized, including: cupsd, ACPI modules & daemon, canna server, 'system message bus', 'hardware abstraction layer', internet supervisor, PCMCIA, postfix mail, powernowd, and Samba daemons. These are the things that don't get listed on the screen when I use Recovery mode. There may be more things that are different; I don't know how to find out.

Here are some errors messages I was able to find in the logs:

** driver failed to call pci_enable_device().  As a temporary ...

Evaluate _OSC Set fails. Status = 0x0005

ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)

Mar 31 02:49:41 localhost kernel:     ACPI-0294: *** Error: Looking up [ACST] in namespace, AE_ALREADY_EXISTS
Mar 31 02:49:41 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_PR_.CPU1._PDC] (Node dfffef40), AE_ALREADY_EXISTS

I don't know what those things mean or if they are related to the problem.

I was having trouble with my printer which turned out to be because permissions weren't getting set. I think it was also because of starting in Recovery mode, because I see that it looks like they should be getting set in 'udev'. 

----------------------------------------------------------------------------------------------------------

I just want to add that it seems that other things seem to be getting worse with apt-get updates and upgrades as the 5.04 release date approaches including: no sound (many people have this problem and the lead developer says it is not important enough to fix before the release), my laptop is overheating now (wasn't before), and other apps that seemed to be working before no longer work or require re-configuration. I would elaborate but I have to get my machine running another distro before it overheats and shuts down again.

---

