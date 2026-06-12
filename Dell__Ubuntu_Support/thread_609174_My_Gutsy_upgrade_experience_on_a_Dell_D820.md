---
title: "My Gutsy upgrade experience on a Dell D820"
date: 2007-11-10
forum: Dell  Ubuntu Support
---

### Post by MarilenCorciovei on 2007-11-10
[The painful upgrade]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/the-painful-upgrade/view")

Everything started with a perfectly working Feisty install on a Dell D820. Pushed again by the little upgrade daemon I decided to do the Gutsy upgrade especially since I did a Edgy to Feisty upgrade some time ago on my old Dell I8600 and everything worked perfectly.
A ruined upgrade

I waited until the end of the week, well I had my share of bad upgrades so I did not wanted to risk a work day, and decided to upgrade. I upgrade tool started and soon it started to complain about various mission or bad configuration files yet it continued. At some point the update window just disappeared and I thought it was the time to reboot my machine. It was already 23:00 when I rebooted my machine just to face a kernel panic. After trying to edit the grub options for the 2.6.22-14-386 without success I rebooted with my old kernel in text mode and tried:

apt-get upgrade
apt-get -f install
dpkg --configure -a

At this point it was clear that the upgrade failed with a core dump.

dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.
Core dumped

I tried for several hours to remove, purge, install various packages without success.

So in the middle of the night I decided to get fetch my other laptop. Fortunately traffic was light at 02:00 so 30 minutes later I found some similar problems which where fixed by removing:

rm /usr/local/lib/libz.so.1*
ldconfig

From now on there was no more core dump in dpkg but I still needed to purge, reinstall a few packages by hand in order for the apt-get upgrade and apt-get dist-upgrade to finish installing and configuring the packages.

Video problems

Now I could boot, around 04:00 with the new kernel but Xorg configuration was completely bad and it showed me a 640x480 window. I had to modify the xorg.conf to match my old one in order to get the nvidia driver to work.

Sound problems
Video was easy to fix but the sound was completely dead. In fact the snd-hda-intel.ko module was not even present. Finally I arrived to this thread and compiled alsa from source. After reboot sound started working again but microphone does not work to date. I will have to find a solution to make it work with Skype until monday.

Wireless problems
I was using ipw3945 in Feisty but the module was again not present. I decided to investigate a bit deeper before going on to install from freshmeat at found that the package containing this modules was not installed so wireless started working again after:

apt-get install linux-ubuntu-modules-2.6.22-14-386
apt-get install linux-restricted-modules


Probably this also contains the snd-hda-intel module.

Suspend/hibernate
Suspend worked perfectly in Feisty but it does not work in Gutsy. There are several links related to this subject but neither fixed the problem.

Finally at 11:00 I had a partial working environment. BAD, BAD, Gutsy.

---

### Post by Triptol on 2007-11-13
Just as a tip:

aptitude update
aptitude dist-upgrade

should do a better job than apt-get upgrade.

---

### Post by el escocés on 2007-11-22
I'm running my latitude d820 on gutsy no probs, everything working apart from the 56K modem, if you need any config help let me know!

---

