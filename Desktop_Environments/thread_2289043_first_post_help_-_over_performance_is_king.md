---
title: "first post help - over: performance is king"
date: 2015-07-31
forum: Desktop Environments
---

### Post by Ndrocchietto on 2015-07-31
Dear All,
hope to write and mainly read a lot of post in this legendary forum.
 first part are my 2 connected questions, second part I present my self


_***First part:***_

I decided to use lubuntu for my notebook to install android studio, but as wannabe developer really creative I need transparency in android studio, but not on other windows.. I thought xfce could fit my needs but the benchmarks lubuntu vs xubuntu are really for lubuntu.

So I would like to stick with lubuntu but also giving a try to xubuntu. 
I understood that Ubuntu lxde is not like lubuntu because in Ubuntu lxde there are some demons, and the apps installed on default are more expensive in terms of resources.
S;) my first question is: 
how do I monitor which configuration of the system is the best? is using $top the best way, or there is other? I need this info because I need to test my first lubuntu fresh version against the change I am going to make

S;) my second question is:
if I want to have fun with $sudo apt-get install xubuntu-desktop(but could be also kubuntu) how can I reverse totally the process? for totally I need I want a clean lubuntu again!
I found this on the net but I do not know if is valid for 14 version but I do not know if is a valid procedure

//this first I would skip as I already have it $sudo apt-get install lubuntu-desktop, or the xubuntu version overwrite something?
$sudo apt-get purge xubuntu-desktop
$sudo apt-get autoremove
$sudo apt-get purge package1 ..packagen //where package1..n are the ones found as difference inside apt-cache depends xubuntu-desktop >~/xubuntu-desktop-depends.txt WITH apt-cache depends lubuntu-desktop >~/lubuntu-desktop-depends( a bash script would help maybe)
):P


really happy to be back in penguinland



_***Second part:***_

I present myself in one bash row: 
$I have Linux experience, I missed Linux since 8 years for prof reasons( Slackware), now having bought an i3 haswell processor notebook.

with a lot of happiness my choice was Lubuntu: a minimal distro, with the power of Linux and a huge community.

---

### Post by TheFu on 2015-07-31
a) welcome.
b) best to ask 1 question per thread - since the knowldge to answer 1 is usually extremely different from the other.
c) When changing desktops, it is best to create a new userid for each so the settings don't clobber each other for related setting files.  If you want to completely remove something you installed usually the **aptitude purge** command will do that for the system, but it will NEVER remove files in your HOME.  The best way I know to get a system back exactly where it was is to create a snapshot through LVM and rollback the snapshot when you are done. That is a little advanced, however.
d) Android development is java. That means a Core i7 with 32G of RAM is needed to be happy.  I know from experience that a Core i5 (1st gen) with 8G of RAM is painful. I couldn't live with it on a laptop. Maybe if everything were on an SSD it wouldn't be so bad? I dunno.
e) there are hundreds of ways to monitor performance. The "best" method is completely subjective based on your use patterns and how you want to see the results.  munin, cacti, sar are commonly used to monitor servers. There are probably 20 other systems.  Top is fine for a snapshot, but that isn't very useful to compare performance over the last day, week, months, years ... That is how professionals do monitoring.

IMHO.

---

### Post by Ndrocchietto on 2015-08-01
> **TheFu said:**
> a) welcome.
b) best to ask 1 question per thread - since the knowldge to answer 1 is usually extremely different from the other.
c) When changing desktops, it is best to create a new userid for each so the settings don't clobber each other for related setting files.  If you want to completely remove something you installed usually the **aptitude purge** command will do that for the system, but it will NEVER remove files in your HOME.  The best way I know to get a system back exactly where it was is to create a snapshot through LVM and rollback the snapshot when you are done. That is a little advanced, however.
d) Android development is java. That means a Core i7 with 32G of RAM is needed to be happy.  I know from experience that a Core i5 (1st gen) with 8G of RAM is painful. I couldn't live with it on a laptop. Maybe if everything were on an SSD it wouldn't be so bad? I dunno.
e) there are hundreds of ways to monitor performance. The "best" method is completely subjective based on your use patterns and how you want to see the results.  munin, cacti, sar are commonly used to monitor servers. There are probably 20 other systems.  Top is fine for a snapshot, but that isn't very useful to compare performance over the last day, week, months, years ... That is how professionals do monitoring.

IMHO.
a)thanks
b)point taken
c) interesting, thank you to share. I guess [SIZE=5][/SIZE]a partition apart looks a bit extreme, how is possible that nobody invented a mechanism that take track of the transaction and package installed from a due date and then allow to move it back? I guess as you suggest at this point just cancelling the new /home/TheFu2 should make the trick.. and thank you because i found a magic word: Fdisk looking up in internet.. how many feelings buried came back to life, how many fears of the past to try to log in distros with lilo and grub that did not work anymore:)
d) please see below *, your comments need further attention IMO
e) what a versatile OS this linux, thank you I will take these suggestions in high value.

* [SIZE=3]**point d extended**[/SIZE]
First of all: Holy Jobby!!!This Lubuntu is the best stuff I ever tried, It is just unbelievable the performance I have compared with the windows 8.1 partition!( and believe me I worked hard to make android studio working there, services uninstalled, start up apps etc etc). What a pain you are speaking from?:)  After 1-2 seconds the CPU skyrockted once in a while to 365% the processor remains at 23- max 30 per cent!!! Debugging is surprisingly fast, even more than my other laptop win 8.1 with I7 4gen/16 G ram!!! (where I did not make any optimization at all). OK i modified udev to connect the usb to the phone instead of the emulator, but still i do not think that in future genymotion or androVM by virtualbox will weight more than 168M of ram.. Ok Java...but this openJDK installed is quite fast indeed.
my pc> is just a cheap 550 eu Aspire V3  1,2kg(2.7 pounds) with 4G ram and an i3 400SU 1,7Ghz, and ok I have SSD that makes things easy... but is unbelievable Thefu, what linus torvalds can make!:) 1000 euro less than the new ios air with the difference I can code on the sun due to the matte screen:)

Anyway in one month that will consolidate more knowledge on the topic, I would like to start a thread on using android studio with lubuntu for i3,i5, chromebooks users or a kinda of tutorial for the android/ubuntu community.
just I am a bit disappointed by the fact that there is a huge cons, the fluidity of linux on scrolling or pinching and zooming remains not fluid at all! but I can forgive Mr Mario Behlings as it looks a linux issue in general as far as I remember 6 years ago.:lolflag:
The shortcuts are amazing and really windows alike, that make them IMO the ideal solution for every window user( except for gamers), I am even surprised Lubuntu is less famous/less installed than Ubuntu.

from now on  I am a lubuntu advocate):P

---

### Post by TheFu on 2015-08-01
/home/TheFu2 would be a bad name - userids need to be all lower-case for many reasons.

As to taking a point-in-time backup - that is easy and there are many different ways to accomplish it.  The quickest requires having some setup in advance - it is called a snapshot and requires the use of LVM. However, using LVM is more advanced than most people are comfortable.
The other ways are just normal backups. There are 500 different ways to do that. Because user files are only stored in the HOME, there aren't really any surprises like with _other OSes_.  A normal userid cannot write to the protected parts of the file system - PERIOD. No surprises.

---

### Post by Ndrocchietto on 2015-08-03
I read it over the historical reasons on lower case userid on terminals on an archilinux forum, that I have to say is also a nice distro

Due to the amazing time contraints( 14 hours work: normal work+ coding at night), I will follow this superior schedule:
1) neating up a bit lubuntu, with my limited knowledge, to make it faster than ever
2) backing up the system with the best backup for dummies tool, that will restore my snapshot working a treat!
3) playing in my free time with Ubuntu LVM snapshot experiments(low priority although kinda of good and challenging skill to learn)
4) playing as a crazy with all the packages to put transparency in Lubuntu
5) if the system slowdown, then restore back up:guitar:, while seeing a movie on the other pc

---

### Post by CantankRus on 2015-08-03
When ever I install [**_[COLOR="#B22222"]metapackages[/COLOR]_**]("https://help.ubuntu.com/community/MetaPackages") like kubuntu-desktop
or packages that install a lot of dependencies that I may want to remove after a short while,
I use the terminal to install (sudo apt-get install [COLOR="#808080"]<package>[/COLOR]) and highlight with the mouse all the packages to be installed.
I then run this command to copy the highlighted packages to a text file.(requires installation of **xsel**)
```
echo $(xsel) > [COLOR="#808080"]xxxx[/COLOR]-packages.txt
```

The xsel command copies all the packages to one line so when I want to remove I open
a terminal and enter "**sudo apt-get remove**" followed by the line from the [COLOR="#808080"]xxxx[/COLOR]-packages.txt file.

---

### Post by Ndrocchietto on 2015-08-04
I am impressed by the amount of knowledge that you share in this forum, and thank you to take some time to make a jpg snapshot!
I will follow your advice as well although I will also take care of making a different userid profile to cancel the user settings

---

