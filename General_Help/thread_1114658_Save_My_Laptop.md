---
title: "Save My Laptop"
date: 2009-04-03
forum: General Help
---

### Post by plurworldinc on 2009-04-03
I find myself in kind of a pickle, and the basic fact I am new to Ubuntu somewhat doesn't help me. I installed 8.04 and upgraded to 8.10 on my laptop after a dual boot that went wrong somewhere. I must say I was very happy when I started working with Ubuntu but now it is becoming somewhat of a mental case.

   First off my wifi went bye bye when a new update knocked out my madwifi. I didn't notic at first because my laptop was connented thought my home system viva on a wired system, but when I had to go away on a trip with out the use of my PC that was a nightmare.

  Another strange problem I could not figure out was my graphic got all weird and I can't play any games or open a number of programs with out the screen going all funny. 

   I am way over my head with this one and have no idea what I am doing, can anybody please save me. I have decided not to give up on Ubuntu or Linux because it's wonderful and scary all at the same time....

 I am working on a Toshiba Satelite with ATI Radeon and AMD 64.

---

### Post by iponeverything on 2009-04-03
> I am working on a Toshiba Satelite with ATI Radeon and AMD 64.

This is still a bit vague. You should post the output of:

sudo lspci
sudo lshw 
sudo cat /var/log/Xorg.0.log

---

### Post by ju2wheels on 2009-04-03
I can answer the first half of your problem.

If you had to manually install madwifi to get your wireless working when you initially installed Ubuntu then chances are that each time the linux kernel gets updated, you will need to install madwifi again. The reason is madwifi is compile against the kernel so when the kernel changes, then you need to recompile and reinstall madwifi. For this reason Id always recommend you have a copy of the madwifi source code and instructions on how to install it in your home folder.

As for the video im not too sure as I havent used ATI cards myself but I do know they are the cards that seem to cause the most trouble with Linux compatibility.

---

### Post by Dejai on 2009-04-03
Hello plurworldinc,
Firstly I would like to know what wireless card you have in your laptop. So please open up terminal and type the following command. 
```
lspci | grep Network
```
if the above command does not work, run lspci and scroll down till you see something like Network controller.

Next run:
```
lspci | grep VGA 
```
if that returns nothing try,
```
lspci | grep ATI 
```

Please post these results here. 

Some other things to try include:
System->Administrator->Hardware Drivers  and check that the proprietary ATI graphics binary is enabled. It may not be installed or something happened during the upgrade. 

Also look at this post, someone else with a madwifi issue when upgrading to 8.10 and his resolution, don't expect this to apply to your card however it may provoke some ideas: [http://www.uluga.ubuntuforums.org/showthread.php?t=970282](http://www.uluga.ubuntuforums.org/showthread.php?t=970282)

Hope this helps.

---

