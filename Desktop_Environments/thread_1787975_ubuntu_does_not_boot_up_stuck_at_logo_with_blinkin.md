---
title: "ubuntu does not boot up stuck at logo with blinking process bar"
date: 2011-06-21
forum: Desktop Environments
---

### Post by pxs096320 on 2011-06-21
Dear friends,
I am a novice to ubuntu. I was just curious to learn more about it. I  have currently installed the ubuntu 11.04 natty narwhal edition through the wubi installer alongside windows 7. I  wanted to just check out what the kde environment had to offer  differently from the default desktop environment which is gnome unity  environment. 

I installed the kde environment using some sudo command given by google.  After using kde environment for a few hours, I just began to feel, I  liked the default gnome environment better (in classic mode) as compared  to kde as I was more used to the former. 

So I uninstalled kde with another sudo command which I got by googling.  At the final step of the uninstallation, I admit I am not sure whether  what I did was right or wrong. There was sth related to 'daemon' that  popped up eventually and I chose yes for that and kde was uninstalled  successfully or atleast that's what I thought. 

But to my horror, when i tried rebooting my laptop to ubuntu gnome, the  blue coloured kubuntu logo was popping once again and I had to go back  to the synaptic package manager and delete sth called the 'plymouth'  package to remove the kubuntu logo. 

Now after doing all these, when I tried booting ubuntu, I was not able  to get to the gnome login screen. The screen was just stuck with the ubuntu  logo and the process bar blinking and gnome never started. 

When I pressed the Esc key to check out what was happening from behind, I  could see that some processes were being checked and there was a [ok]  after everything and there was a [FAIL] next to "starting CPU interrupts  balancing daemon". And the terminal screen ended with "stopping system V  run level compatibility". I am not sure if this might be the root cause  of blocking the boot-up. But I couldn't get a screenshot of those  intermittent terminal screens as I was not in a position to type in any  commands such as fbgrab which can be used to grab a screenshot of the  terminal screen.

Eventually after intense googling, I figured how to manually configure  gnome to start up. I pressed the Cnt + Alt +F1 as soon as the white  ubuntu logo popped up and after logging in into my ubuntu account  through the terminal interface, I typed in the following things.
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
and then voila I got the gnome login screen. I temporarily heaved a sigh  of relief. (by the way I saw something flash quickly on the terminal  moments before it went to the gnome login screen like "you need not init  this way or sth"..I just couldn't catch sight of it properly as it  flashed only for a few moments)

But I am not satisfied. Obviously there might be a way to set this  problem right isn't it? Kindly someone pls throw some light on this issue. I want gdm to be automatically  activated during boot. Its a big pain to manually configure  it everytime I boot. Is it possible to do a windows restore to set the ubuntu right? But I saw in some forums mention that something called the boot.ini will botch up if we perform a system restore in win 7.

Someone pls help me by telling me a method that does not involve  uninstalling ubuntu and reinstalling it. This is because I have done a  lot of tweaks, optimisations and installed lot of apps in it. I do not  have a system image backup as well. So it will be a nightmare to do all  these things over and over again. The mistake or rather the drawback from my side is I just have my laptop alone and do not have another standalone desktop to experiment with linux.

---

### Post by pxs096320 on 2011-06-23
Bump....no reply yet...anybody willing to help out here? Thanks.

---

### Post by amadib on 2012-01-11
Did you ever solve this?

---

### Post by adityamagadi on 2012-01-11
boot in as a live session user thru ur ubuntu DVD n try re-installing ubuntu...

---

