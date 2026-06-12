---
title: "[SOLVED] Making Custom Live CD/DVD from all files on my hard drive"
date: 2007-09-15
forum: Development CD/DVD Image Testing
---

### Post by saj0577 on 2007-09-15
HIya guys,

I think this is the right area to put this question if not i would be greatful if someone could move it to the correct area.

Right here is my question:

I currently have a box with ubuntu installed on it along with a few other programs such as a custom AMP with all my config files and settings. What i want to do is make a custom CD/DVD(most probably DVD) which i can make a live cd of my computers exact file structure, i.e every file/folder/setting/program/etc.. on the computer. Then when i run this live cd on a machine it would be exactly the same as my current set up and files on the system (as if i was not running the live cd at all.) 

Also if as well as these files being present in the live cd, if all the files could be installed on the machine which i install ubuntu from my custom live cd from that would be great. (so much like copying my whole hard drive to another computers hard drive [but also have the portability of being able to use it as a live cd].)

Hope that is clear enough and it helps you to help me
Thanks in advance

Saj

---

### Post by sonhadorpr on 2007-09-17
I understand what you are trying to do, I'm trying to do the same thing, but no such luck yet.
I have a couple of sites with some instructions, but since I'm a newbie, I get lost pretty quick, maybe you know what to do , and are able to do this, and let me know how it turns out.
Here are the sites.

[http://www.xastir.org/wiki/index.php/HowTo:Ubuntu_6.10_LiveCD](http://www.xastir.org/wiki/index.php/HowTo:Ubuntu_6.10_LiveCD) <-- I think it's the best.
[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)
[http://www.google.com.pr/search?q=live+CD+creation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com.pr/search?q=live+CD+creation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
[http://librenix.com/?inode=3608](http://librenix.com/?inode=3608)

Yet another Ubuntero @ ubuntu-es.org told me to install a certain program to help you do this, however it's in Spanish, and the program mentions another Distro (Tuquito Linux), and I haven't tried it, since I'm a newbie, and don't want to venture out into other Distros, just yet.  The app is called Garfio, and you can get it @ [http://www.garfio.org.ar/](http://www.garfio.org.ar/)
Hope this can point you in the correct direction, even though I'm not telling you much.
Please, if you are successful in doing this, share the knowledge.

Have a great Ubuntu day!!!
ROM

---

### Post by saj0577 on 2007-09-17
Hiya m8, I will look at those website tomorrow (i only got back today so am just chillin).


If i get any luck i will post it on the forums for everyone else to benefit from.

I have sent you a private message with my msn address if you wish to add me so we can talk about it.

Good Luck to everyone if you have the same problem please post it so we can all work together.

Saj

---

### Post by Scott00 on 2007-09-18
I'm trying to do the same thing... I want to make a livecd/install disk with some extra programs pre-installed and a customized default appearance (as well as uninstalling some so it all fits)... But I don't know where to begin in compiling it as a liveCD or what to change in the ISO to match my install... The biggest issue is that some of the files that I need to have are user files located under /home/user/.* so I wouldn't know how to go about doing that.. I'd be happy just with being able to compile it for the customized appearance though if possible.


Thanks for any help.

---

### Post by smartboyathome on 2007-09-19
Remastersys may be what you all are looking for.
[http://www.linuxmint.com/wiki/index.php/Remastersys](http://www.linuxmint.com/wiki/index.php/Remastersys)

---

### Post by saj0577 on 2007-09-19
> **smartboyathome said:**
> Remastersys may be what you all are looking for.
[http://www.linuxmint.com/wiki/index.php/Remastersys](http://www.linuxmint.com/wiki/index.php/Remastersys)

On that can you also add files that you want to be installed on install, much like the "Examples" folder that is created in your home direcotry when you install it. Also not only install the programs on install i also want them to have all my pre adjusted configuration files.

Saj

---

### Post by Fragadelic on 2007-09-20
I am the guy that created Remastersys.

It is still a work in progress at this point.  I have asked on the Ubuntu Launchpad site for help with casper and ubiquity which the livecd uses for booting and installation.

The script I wrote is currently written in Bash but I would like to port it over to python which is the standard scripting language in Ubuntu.  Also working on a frontend for it as it is currently just a commandline tool.

Any options you think could be added, just let me know and I'll see what I can do.

I originally built the script on Kubuntu but didn't get much of a response on the kubuntu forums so I gave up on them.

I've been working with the Linux Mint folks who have helped me test it more than anyone else but I need some good documentation on casper and ubiquity to be able to refine the process.

There is also a size limitation at the moment due to a bug in the way squashfs works but I am working on a workaround to be able to fully use the entire dvd.

---

### Post by Rob-e on 2007-10-14
maybe this will help??
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

---

### Post by saj0577 on 2007-10-17
I would prefer not to use a program as they restrict me.

Saj

---

### Post by Computer Cat on 2007-10-27
Well, I don't mind programs. Could the maker of Remastersys please enlighten us on how to obtain the debian package for Ubuntu 7.10? Thank you!

---

### Post by brennydoogles on 2007-10-28
> **Computer Cat said:**
> Well, I don't mind programs. Could the maker of Remastersys please enlighten us on how to obtain the debian package for Ubuntu 7.10? Thank you!

I agree. Another question about Remastersys... while using the dist option, will it capture things such as installed audio/video codecs and fonts, or will it only capture installed programs? Also, is there a way to remove programs from the list of what you want on the new  live distro? For example, I have a few programs installed that do not have a .deb available, and would be broken by the dist option because of configuration files being located in the home folder. Thanks for your help!

---

### Post by po3 on 2007-10-28
very informative article, thanks

---

### Post by smartboyathome on 2007-10-28
> **brennydoogles said:**
> I agree. Another question about Remastersys... while using the dist option, will it capture things such as installed audio/video codecs and fonts, or will it only capture installed programs? Also, is there a way to remove programs from the list of what you want on the new  live distro? For example, I have a few programs installed that do not have a .deb available, and would be broken by the dist option because of configuration files being located in the home folder. Thanks for your help!

Use the Romeo repo. Someone (a spammer >:() got rid of the instructions on the article, but if you browse back a little ways in the history, you should be able to find it. Anyway, you would have to uninstall the programs you don't want on the livecd, and it basically put everything on the livecd besides things in your /home folder, so make sure your configurations are system wide. Also, there will be a new version out for Remastersys soon which doesn't require the origional CD, so wait if you can.

---

### Post by brennydoogles on 2007-10-28
> **smartboyathome said:**
> Use the Romeo repo. Someone (a spammer >:() got rid of the instructions on the article, but if you browse back a little ways in the history, you should be able to find it. Anyway, you would have to uninstall the programs you don't want on the livecd, and it basically put everything on the livecd besides things in your /home folder, so make sure your configurations are system wide. Also, there will be a new version out for Remastersys soon which doesn't require the origional CD, so wait if you can.

I went ahead and downloaded reconstructor, because it seems like it is more readily usable at this time, but when the new version comes out I would love to help test it.

---

### Post by smartboyathome on 2007-10-28
> **brennydoogles said:**
> I went ahead and downloaded reconstructor, because it seems like it is more readily usable at this time, but when the new version comes out I would love to help test it.

I have had tons of bad luck with Reconstructor, I much rather set up my system and then use Reconstructor to make a LiveCD from it. Best of luck to you!

---

### Post by puccaso on 2007-10-29
how about creating a livecd from my current installed system on my HD ?? liveCD/liveDVD/liveUSB whatever... can i get my current system running as a live**?

---

### Post by smartboyathome on 2007-10-30
> **puccaso said:**
> how about creating a livecd from my current installed system on my HD ?? liveCD/liveDVD/liveUSB whatever... can i get my current system running as a live**?

You can do that with Remastersys, too. :)

---

### Post by ankursethi on 2007-11-03
Erm, PCLinuxOS comes with a remastering tool by default called "remasterme". In fact, PCLOS is *meant* to be broken, twisted, bent and remastered all the way to hell and back again. I use Ubuntu on the desktop, but if I'm going somewhere and need a Linux to work, I install a remaster of PCLOS to my USB and get going.

[http://www.pclinuxos.com](http://www.pclinuxos.com)

PS : I hope nobody minds the shameless PCLOS promotion :)

---

### Post by Fragadelic on 2007-11-11
I have released Remastersys 2.0-2 and it starting with 2.0-1 it has had a gui.

Add this to your /etc/apt/sources.list

# Remastersys
deb [http://www.remastersys.klikit.org/repository](http://www.remastersys.klikit.org/repository) remastersys/

The new homepage is:

[http://www.remastersys.klikit.org](http://www.remastersys.klikit.org)

The version on the Romeo repository of Linux Mint is outdated and shouldn't be used.

Take a look at the website and either post here or on the remastersys forum if you have any questions.

---

### Post by jobsonandrew on 2007-11-29
im currently using remastersys 2 to make a liveCD backup of my ubuntu 7.04 that i installed using wubi ([www.wubi-installer.org](www.wubi-installer.org))

when it says "this will take a while, so be patient" how long is a while? cos my laptop has been churning away at 100% CPU usage for about 5 hours now..

any chance of a progress bar in the next release? lol anyone think that im waiting too long for this and that somethings up?

---

### Post by smartboyathome on 2007-11-29
It used to show the progress of it when using the console version. But it also depends on how much stuff there is as to how long it will take. If there is a lot of stuff on it, it will take a while.

---

### Post by saj0577 on 2007-11-30
> **puccaso said:**
> how about creating a livecd from my current installed system on my HD ?? liveCD/liveDVD/liveUSB whatever... can i get my current system running as a live**?

Thats my goal too.

Saj

---

### Post by gb64 on 2007-12-01
Yesterday, downloaded latest Remastersys into Ubuntu 7.10. Setup Ubuntu just like I wanted, added TrueCrypt and the EasyCrypt GUI for TrueCrypt, plus a small number of other programs, then ran Remastersys Backup option. Within about 30 minutes I had my own livecd which ran with no problem.
The operational CD uses my regular login, configurations, and settings. Perfect!

Make sure you get the latest version from above posts by Fragadelic.

---

