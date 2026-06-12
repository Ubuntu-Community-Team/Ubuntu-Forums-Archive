---
title: "Ubuntu 5.10 vs 5.04"
date: 2005-12-27
forum: General Help
---

### Post by lomaxxf3 on 2005-12-27
I currently have Ubuntu 5.04 and am waiting for my shipment of 5.10 cd's. I think that once I install 5.10 onto my laptop, all the problems that I have of the current build that I possess will be resolved since it will be updated. The main problem I have is installing any program and using the synaptic program updater program or whatever it is you use to download programs from the linux database. Do you guys think I'll have less of this problem after updating my ubuntu system?

OFF TOPIC: What program, that works on ubuntu, can serve the same purpose as iTunes on Windows, including playing AAC files and building a library of files?

---

### Post by Swab on 2005-12-27
[QUOTE=lomaxxf3]I currently have Ubuntu 5.04 and am waiting for my shipment of 5.10 cd's. I think that once I install 5.10 onto my laptop, all the problems that I have of the current build that I possess will be resolved since it will be updated. The main problem I have is installing any program and using the synaptic program updater program or whatever it is you use to download programs from the linux database. Do you guys think I'll have less of this problem after updating my ubuntu system?

OFF TOPIC: What program, that works on ubuntu, can serve the same purpose as iTunes on Windows, including playing AAC files and building a library of files?[/QUOTE]

Can you be more precise in the nature of the problems you are having... maybe someone here can help.  

Amarok is similiar to iTunes... but I don't know if it will play AAC, and definitely not the apple encrypted ones.

---

### Post by pauljwells on 2005-12-27
Firstly, if you have a fast internet connection then you shouldn't install 5.10 over 5.04. All tou need to do is edit /etc/apt/sources.list. Change everything that says 'hoary' to 'breezy' except for the first line, which refers to the CD, which you want to disable by typing a # in front of it.
Then apt-get update then apt-get dist-upgrade. Finally, reboot (for the new kernel). Try searching for these specific commands in these forums and you'll find plenty of info.

There are two popular programs for 'iTunes' functionality (although it would be hard to beat iTunes, which s one of the best programs ever written by anyone for anything :) ) The default, and my preference, is Rythmbox, you need to install the right plugins to give AAC playback, search for the faad packages in synaptic, you might need to enable some extra repositories, see [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

The other program is Amarok, which is a much 'fuller' GUI than Rythmbox, but although it will play aac files, it is better at mp3.

---

### Post by lomaxxf3 on 2005-12-27
[QUOTE=Swab]Can you be more precise in the nature of the problems you are having... maybe someone here can help.  

Amarok is similiar to iTunes... but I don't know if it will play AAC, and definitely not the apple encrypted ones.[/QUOTE]

Sorry about that. Everytime I want to install a program through the Terminal, it asks me where the file is located, but each time it tells me that the file does not exist when I type up the file's location. Sometimes it asks me to direct it to a specifically-named file and then I would rename the file, but still the same problem persists. I'm thinking that maybe the 5.10 synaptic program downloader program is more up-to-date and will allow me to install programs effortlessly with  Terminal. Can someone confirm this or otherwise? 

Otherwise, tell me what the problem may be. I have tried reinstalling Ubuntu then trying to install a program (i.e. Realplayer and GTKpod) but it still never works. (As for Realplayer, I can only run it by clicking on the executable in the extracted folder; I want it to appear in the programs list by installing it properly) Thank you.

P.S. Sorry that my lengthy posts; I tend to this all the time; Hopefully this amount of information will help you help me.

---

### Post by fordfan753 on 2005-12-27
[QUOTE=lomaxxf3]Sorry about that. Everytime I want to install a program through the Terminal, it asks me where the file is located, but each time it tells me that the file does not exist when I type up the file's location. Sometimes it asks me to direct it to a specifically-named file and then I would rename the file, but still the same problem persists. I'm thinking that maybe the 5.10 synaptic program downloader program is more up-to-date and will allow me to install programs effortlessly with  Terminal. Can someone confirm this or otherwise?[/QUOTE]

Can you give a demo command of how you are trying to install via the command line? Maybe you're doing something wrong, because I've never seen anything like that happen before...

To answer your question Breezy does have an added updater program, which you either love or hate, it's pretty easy to use, and most people like it.

---

### Post by sciurus on 2005-12-27
*sudo apt-get install gstreamer0.8-faad* is the command that will make Rhythmbox and Amarok support aac-encoded files in Breezy. It is in the multiverse repository, so once you have Breezy you would need the line *deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse* in */etc/apt/sources.list*. After this line is added, you should also be able to install gtkpod from universe with *sudo apt-get install gtkpod*.

---

### Post by lomaxxf3 on 2005-12-27
[QUOTE=sciurus]*sudo apt-get install gstreamer0.8-faad* is the command that will make Rhythmbox and Amarok support aac-encoded files in Breezy. It is in the multiverse repository, so once you have Breezy you would need the line *deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse* in */etc/apt/sources.list*. After this line is added, you should also be able to install gtkpod from universe with *sudo apt-get install gtkpod*.[/QUOTE]

I've heard the term "repository" many times and I still cannot seem to fully grasp the concept. Can someone explain in n00b terms? Thanks.

---

### Post by ts. on 2005-12-27
[QUOTE=lomaxxf3]I've heard the term "repository" many times and I still cannot seem to fully grasp the concept. Can someone explain in n00b terms? Thanks.[/QUOTE]
A repository for APT is a server that has a bunch of .deb packages on it. You need to enable repositories in order to get things from that server through APT. Multiverse and Universe are standard Ubuntu repositories that you can enable through the GUI in Synaptic; others can be added by editing the sources.list file (use the commands *sudo gedit* (or other favorite text editor) */etc/apt/sources.list*)

---

### Post by Swab on 2005-12-28
[QUOTE=lomaxxf3]I've heard the term "repository" many times and I still cannot seem to fully grasp the concept. Can someone explain in n00b terms? Thanks.[/QUOTE]

Check out these 2 pages in the wiki:

[LIST]
[*][Repositories]("https://wiki.ubuntu.com/Repositories")
[*][AddingRepositoriesHowTo]("https://wiki.ubuntu.com/AddingRepositoriesHowto")
[/LIST]

The wiki really is your best friend!

---

