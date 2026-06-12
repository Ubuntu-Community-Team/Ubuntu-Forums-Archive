---
title: "Cannot load gui"
date: 2010-08-20
forum: Desktop Environments
---

### Post by spacegravity4me on 2010-08-20
Hi everybody.
I have an old desktop that wouldn't run 7 very well and I decided to install ubuntu on it. It's the latest version.

I installed it fresh on the hard drive

I then began having a problem with my monitor saying that there was no signal and then going to sleep after the boot process.

I found this site here [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html")
and did what it said. I edited the grub during boot, got back to the gui and then tried editing the grub permanently. I did the sudo thing in gedit and changed it from "quiet splash" to "quiet splash nomodeset".

Foolishly thinking my problems would be behind me I restarted the machine.

Now when the computer starts grub loads and then I see a purple screen that says ubuntu on it, followed by 

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 136919/2359296 files, 681365/9423104 blocks
* starting apparmor profiles
skipping profile in /etc/apparmor .d/disable: usr.bin.firefox
                       [OK]
*Setting sensors limit [OK]
*Speech-dispatcher configured for user sessions
*Starting Common Unix Printing System: cupsd   [OK]
*PulseAudio configured for per-user sessions
*Enabling additional executable binary formats binfmt-support[OK]
*Checking battery state...

The stars next to speech-dispatcher and pulseaudio are yellow by the way.

This screen will flash about 5 times and then I get a screen that says Ubuntu 10.04 LTS space-desktop tty1

space-desktop login:


That's it. Someone please help me before I destroy this thing. I really don't know what to do now. thanks.

---

### Post by Zeike on 2010-08-20
once you boot up and get to the console login prompt try pressing 'ctrl-alt-f7' (if that doesn't work try ctrl-alt-f8).

If both of those print you to black screens, you can use ctrl-alt-f1 to get back to the console login.  There you might try logging and typing "sudo /etc/init.d/gdm restart"

---

