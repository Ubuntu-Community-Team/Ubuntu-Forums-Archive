---
title: "dell latitude d630"
date: 2012-04-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gordonjr05 on 2012-04-08
Hi i think im in the right place im new to Ubuntu and i was wondering if someone could tell me how to install all driver for the computer that i got and the specs are as followed 
Intel 965 express chip set

dell wireless 1390 wlan card 

Intel core 2 duo 1.8ghz

4 gigs ram 
those are the specs that i need help getting drivers for 

and the others things i was wondering is if i could get a newbie guide to install and run wine 
becuase i play world of Warcraft and would like to get it running as well could someone link me some free programs i could use that are similar to Photoshop and Dreamweaver and i was wonder if you can get blender to run under Ubuntu thanks for help guys im a complete noob lol 
thanks Gordon Albert
also i do have Skype) if it be easier

---

### Post by Paddy Landau on 2012-04-09
Do you have Ubuntu already installed? Or are you trying to find drivers before installing Ubuntu?

Ubuntu comes with many drivers, and most machines will work "out of the box". Once Ubuntu is installed, you can open *Additional Drivers*. It will automatically look on the Internet to see whether or not there are proprietary drivers for your machine. If so, it will list them, and you can enable each one separately if required.

If you have not yet installed Ubuntu, the easiest thing to do is to burn a Live CD or a Live USB (the instructions are on the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download")). Boot from the CD or USB and choose to try Ubuntu (this option will not change your computer at all). Experiment and use the Internet; you will quickly find if anything does not work.

Regarding Wine, you need to know a few things.

[LIST]
[*]Wine is not a Windows emulator. While some Windows programs work well, many work poorly and most do not work at all. Search the [Wine application database]("http://appdb.winehq.org/") to see whether or not your program is likely to work (if your program is not listed, it has not been officially tested). Sometimes, there is an alternative open-source program to replace the program you want. If you really must use Windows programs, perhaps you need to stick with Windows?
[/LIST]

[LIST]
[*]When installing, running and deinstalling Windows programs through Wine, bear in mind that Wine is quite complicated. Fortunately, there is a program that is a front-end for Wine, hiding its complexity. To this day, I do not know how to use Wine, but I use it anyway by using PlayOnLinux. PlayOnLinux should be installed on your Ubuntu already, but if not, open Ubuntu Software Centre and install it. Then always use PlayOnLinux to install, run and deinstall Windows programs -- it is very much easier.
[/LIST]

[LIST]
[*]If you need to use Windows programs but you'd also like to use Ubuntu, you can install Ubuntu as a *dual boot* -- in other words, you split your hard drive into two (the Ubuntu installer will do this for you if you don't know how to do it yourself). Ubuntu is installed alongside Windows. Each time you boot, you are given the choice as to whether you want to boot into Windows or Ubuntu. Ubuntu can read and write your Windows folders, but Windows will not be able to read or write your Ubuntu folders.
[/LIST]

---

