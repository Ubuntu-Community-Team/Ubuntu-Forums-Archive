---
title: "new to ubuntu ((few Q)) - toshiba u300 -130"
date: 2008-12-11
forum: General Help
---

### Post by htoofe on 2008-12-11
hello there..
first of all I wanna thank you for you great help and support for the new users to ubuntu ^_^
----
I decided to install ubuntu 8.10 on my notebook toshiba u300-130 with 250GB harddisk and 2GB ram I need some help on basic things.. I wanna use all the 250GB for ubuntu so there will not be windows xp or something
----
1- the partions ((root,home,swap,boot)) what sizes,type should I give to each one of them.. ex.((120GB root, 120GB home,4GBswap,1GB boot)) :/
2-I'm not sure what is the home and the root partions are so plz try to explan to me.. :/
3-the programs and apps where does it go is it in the home or the root.. and if I tried to do reinstall is that mean all my programs and apps will be deleted..??
4-is it good to have xubuntu,ubuntu and kubuntu at the same time..??
5- kde=kubuntu ,xfce=xubuntu, gnome=ubuntu is that right..??
6-the edubuntu looks like ubuntu but with more apps for student
so I don't wanna install it where can I find the packages or the apps so that I can install them :)
7-Am I going to face a problems or bugs like when I play video my laptop will freeze or the wifi won't work or the kubuntu crash when I change the desktop efficet something like that :/ ??
8-Did you try ubuntu on your toshiba u300 - 130 before and did you face problems..??

that's set for now.. and thx.. for your helping.. :)

---

### Post by jake1017 on 2008-12-11
I will try and answer all your questions as best I can.

1. Root (I think you mean the Main File System) should be given a minimum of 10GB but more if you wish to install lots of apps. But if you are talking about the file "Root" on the File System than you should give it nothing. 
Home doesn't need anything unless you plan to store files (videos, documents, music, photos, etc). If that is what you want than give it a large amount of space depending on what you plan to store in it. 
Swap doesn't need that much space since you have a reasonable amount of ram, 1GB should suffice. 
I haven't heard or anyone giving Boot its own partition so I wouldn't worry about it.

2. Home contains one directory for each user on the system, in which desktop and user-related settings are stored (Linux equivalent of My Documents).
Root is the home directory of the root user (root is a user that is default on Unix systems and has no user restrictions). 

3. The 'usr' folder usually contains apps that you install.
If you reinstall Ubuntu then all your apps will be deleted.

4.No. You only run one at a time. Choose one with a interface that you like.

5.Yes, you are correct.

6.You can find them through the Synaptic Package Manager.

7. It is possible and if you encounter any bugs just report them on this site and someone should be able to provide a solution.

8.I can't answer this question as I don't have your model of laptop.

Hope I helped.

---

### Post by albinootje on 2008-12-11
> **htoofe said:**
> 
3-the programs and apps where does it go is it in the home or the root.. and if I tried to do reinstall is that mean all my programs and apps will be deleted..??
4-is it good to have xubuntu,ubuntu and kubuntu at the same time..??
5- kde=kubuntu ,xfce=xubuntu, gnome=ubuntu is that right..??
8-Did you try ubuntu on your toshiba u300 - 130 before and did you face problems..??


A quick reply for those questions :
( 3 ) normal programs go in sub-directories in /usr
smaller programs needed to boot and for basic system-administration are in /bin and /sbin
( 4 ) I've used ubuntu and kubuntu on one system quite some time ago, 
i think i installed ubuntu first, and then ran : sudo apt-get install kubuntu-desktop which was quite OK except that the icons inside openoffice were a little bit messed up.
I've also used ubuntu and xubuntu without problems on the same machine last week.
( 5 ) correct
( 8 ) 
Here's your laptop mentioned with Ubuntu :
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/272292](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/272292)

 jmachado wrote on 2008-11-05: (permalink)

--- begin quote ----------------------
I have the same problem lemonidas.

My problem:
The volume goes up to full or empty when I touch the volume dial, and the OSD keeps flashing and the keyboard gets disabled/freezes, but the mouse works.
Everything worked fine on 8.04.
This is a fresh install of 8.10.

My hardware and software:
Toshiba U300-130
Linux jmachado-ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
--- end quote ------------------------

That sounds pretty good! :)

---

### Post by htoofe on 2008-12-11
jake1017,albinootje

thank you v.much for you help..

so now the partions will be ((180GB root,60GB home)) :) I'm not sure about the type tho.. :/

any ideas how to packup my apps and programs to external harddisk so I can use it when needed.. :D

---

