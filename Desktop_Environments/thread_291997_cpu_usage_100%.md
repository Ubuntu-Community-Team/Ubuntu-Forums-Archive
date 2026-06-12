---
title: "cpu usage 100%"
date: 2006-11-03
forum: Desktop Environments
---

### Post by mikael_b on 2006-11-03
Hi,

I have problem with Xorg, it tend to use 100% of my cpu as soon as I try to drag a window or just to scroll in the web browser.

Anyone know how to fix this?

I am running Intel core 2 duo with ati radeon x3000

---

### Post by mikael_b on 2006-11-03
Anyone that know how to solve this?

Please, i really need help with this. Cant run ubuntu when the cpu is at 100% as soon as I try to do something.

---

### Post by elv on 2006-11-03
Isnt this the nautilus cpu bug  [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684)

You can check the System manager (System-Admin-System Monitor) and see if it is nautilus or not, if it is you can kill it to regain your cpu.

Hopefully this bug will be solved soon than later

---

### Post by mikael_b on 2006-11-03
> **elv said:**
> Isnt this the nautilus cpu bug  [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684)

You can check the System manager (System-Admin-System Monitor) and see if it is nautilus or not, if it is you can kill it to regain your cpu.

Hopefully this bug will be solved soon than later

Ok, so there is a process called nautilus, i tried to kill it but it just restarts... and continue to work bad..

The link you posted was regarding high cpu usage when downloading a file. My problem is with high cpu usage when i drag a window. The cpu is at 2% then i try to drag a window in circles and wop and it is at 100% of cpu usage.

---

### Post by elv on 2006-11-04
Nautilus is the filemanager for Gnome.
And it should start straight away after you killed it.
This may be a shot in the dark but have you tried the smp kernel.
Have no idea if it will help or not, but you should be using that kernel anyway since it is better for your CPU.Also what graphic driver are you using

---

### Post by mikael_b on 2006-11-04
I have already tried to install linux-686-smp but I still have the same problem.

How do I see which drivers i'm running?

Maybe I should uninstall Nautilus and install another filemanager if there is any?

---

### Post by elv on 2006-11-04
Here is a Howto for the latest Ati driver [http://www.ubuntuforums.org/showthread.php?t=204910&highlight=radion+drivers](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=radion+drivers)

Also using another filemanager would most likely not be enough as nautilus is also the desktop....but you can always try.
Thunar seems to be really popular here.
[http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)

If you like Thunar and want it to replace nautilus totaly, you can apt-get the Xubuntu packeges, then you would have Xfce as desktop and Thunar as a filemanager

---

### Post by mikael_b on 2006-11-05
So, for running Thunar I need to change from ubuntu to Xubuntu?

---

### Post by anakin513 on 2006-11-09
> **elv said:**
> Isnt this the nautilus cpu bug  [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684)

You can check the System manager (System-Admin-System Monitor) and see if it is nautilus or not, if it is you can kill it to regain your cpu.

Hopefully this bug will be solved soon than later
It sure was for me and there are deb files in the bug report to fix the issue.  Now nautilus is very well behaved.

Seems to happen when you have a file window open and a file is being written to.

---

### Post by Dual Cortex on 2006-12-03
Which one out of all of these are we supposed to install?
[http://people.ubuntu.com/~seb128/debug/54684/](http://people.ubuntu.com/~seb128/debug/54684/)

---

### Post by warri0r on 2007-02-12
> **Dual Cortex said:**
> Which one out of all of these are we supposed to install?
[http://people.ubuntu.com/~seb128/debug/54684/](http://people.ubuntu.com/~seb128/debug/54684/)


yeah .... some one guide me to install these updates/update.

which file i need to download

how can i update with those files

plz help :(

NOTE: i dont want to download the files listed in the update-notifier as whenever i run tat to download files, ubuntu wont start on reboot.
:(

---

### Post by warri0r on 2007-02-13
~bump


sorry , plz help me fixing this :(

---

### Post by BkSlave on 2007-12-01
I finally found it!! Some one else with the exact problem i have!.......Done ALOT to sort this one out but ill try and trim it down...In the begining...My m8 built me this awsome pc lst march and it was great..untill i installed an activeX control (and no not from porn site!) Usual msg re-start for changes to take effect, I did and became trapped in a reboot cycle (continuously within seconds) my only option was to enter bios, change 1st boot to DVD and ran my Xp cd formatted my drive (deleting prev partition) Sorted all my Drivers, Updated my bios etc..Since then Ive noticed (After multible Formats) My cpu sky rockets (usually 60%ish) when dragging a window across the desktop or over an HTML...ok but running Css c&c3 etc it loves, runs beautifuly! Back to windows and weve got probs again but very inconsistant can run super super fast but then its searching for control panel or my computer! (lil torch thing) again can be litt minute or two or a sec also my start ups been diabolical!! Im thinking Bios settings or OS settings??...hmm now my system is 
AsRock ConRoeXfire-eSata2 (MotherBoard)
Intel Core2 Duo E6300 1066 MHz FSB 2 MB L2 Cache (2@1.86GHZ)
3Gig DDR2 RAM (excesive but its getting quite cheap!)   Sorry for long post  Hope you can help! ;D
Geforce 7600GT 
Sata2 HDrives  
O.S Windows Xp Proffesional SP2 (Genuine and fully updated)
.....Yet it thinks its a biddy at times! (I seem cheerfull but maaan in need help!!)

---

### Post by glotz on 2007-12-01
> **mikael_b said:**
> So, for running Thunar I need to change from ubuntu to Xubuntu?No.

(offtopic: my cpu usage is almost 100 all the time but that's because I fold, see signature and join the effort! ;) )

---

