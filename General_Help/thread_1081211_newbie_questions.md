---
title: "newbie questions"
date: 2009-02-26
forum: General Help
---

### Post by miguelp on 2009-02-26
Hi,

I've got many questions since I'm a new linux user, but just gonna point out a few of them there are more urgent.

I've installed ubuntu 9.04, and the major part of the software i need, i was planning to install windows as well but since i just use it to run flash IDE and Photoshop, decided to go with virtualBox. Now i'm not much off a command line guy (need some time to get a better grasp at it) so some things are dificult to me.

**Question:**
1 - at this moment i have 2 partitions "linux swap" and the main one "ext3", and have some free space on the hard drive that was for windows, now i wanna use that space, and as far as i see i have 2 options, either i expand the "ext3" using the live CD (but i'm afraid to loose data) or move the /home directory to a new partion. what should i do? and if the safer option is to move the /home how do i do it without breaking the applications i've installed so far?

2 - As a windows user i used to have some icons on the desktop for the most used apps, and locations. How do i make a shortcut and aplly an icon to a location? for example my server root folder (/var/www) ?

3 - this one is a bit tricky to me, i've installed virtualbox and winXP on it, but i cant share my internet connection nor see any shared folders from the host machine. I shared the folder /var/www but once i run the virtual machine i cant see it inside... maybe because of the network interface isn't working properly. How do i solve this? 

And that's it for now... I'm sorry to fire up these many questions at one time but i really need to get this running as fast as i can.

Thanks in advance.

---

### Post by opscure on 2009-02-26
1. [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

2. Right click your desktop and create launcher.  In the command portion type: nautilus /var/www/

3. check this out (page 4ish) for info on sharing folders through virtualbox: [http://www.pclinuxos.dk/pdf/virtual_box_how_to_XP.pdf]("http://www.pclinuxos.dk/pdf/virtual_box_how_to_XP.pdf")

---

