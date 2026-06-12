---
title: "a setup guide for breezy badger"
date: 2005-12-02
forum: Desktop Environments
---

### Post by irish rebel on 2005-12-02
This tutorial is my repayment to the linux community, Back in 1993 when I first started with linux  there were just forums and newsgroups mostly on usenet .
My distro of choice today is Ubuntu .Why? Simply put its great  , so here goes my tutorial , the aim is to have you up and running with a complete system in 3 hours or less.
My needs: I have to rip my dvd collection, I have over 200 cd's that I have to rip, I make dvd videos for customers weddings and parties. I play nintendo and n64 games on my pc also I run a successful linux consulting business from my home office.

My Computer: Asus 64 bit motherboard , 2 giggs ddrx400mhz ram, 2 500 gig maxtor hdd, nvidia fx 5500 256mb video card.

installation of ubuntu, self expanitory takes 45 mins.

STEP1 As soon as you are finished install do a update ,next go to [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

download automatix and install it will change your repositories and give you ability to install libdvd.css
and mplayer and w32 codecs as well as sun java 1.5 and flash and swp plugins.
Go to [http://www.codeweavers.com/products/cxoffice](http://www.codeweavers.com/products/cxoffice)
download the 30 day evaluation or use wine I prefer to pay for something that is polished and works!
when you download the file right click and go to properties  select permissions tick off execute.
Now double click on it and it will lead you thru the install in about three mins.
Next go to [www.afterdawn.com](www.afterdawn.com)
and download DVDshrink, double click on the file when it finishes downloading and crossover will guide you thru the install. Now you can shrink your legally owned dvd and later burn it.

I love mplayer so go to synaptic do a search for mplayer use the 686 file , then search for libdvdcss click on that file, then search for mplayer fonts include that and lastly w32 search install all these thru synaptic. This will play pretty much all your media files.

To get rhythmbox to play mp3's go back to synaptic search for gstreamer install the file that says all plugins , dont forget to install lame now you are set.

for a video editor I use lives as cinelerra is very needy in terms of hardware so go here

[http://lives.sourceforge.net/index.php?do=downloads&PHPSESSID=7816803bfd929d2c9bd824a01b4e5699](http://lives.sourceforge.net/index.php?do=downloads&PHPSESSID=7816803bfd929d2c9bd824a01b4e5699)
There are now LiVES test packages for Debian (main/unstable/testing): [http://sentinel.dk/linux/debian/packages/lives/](http://sentinel.dk/linux/debian/packages/lives/). It is also available through apt-get. Debian users may add this line to /etc/apt/sources.list:

deb [http://sentinel.dk/debian/](http://sentinel.dk/debian/) unstable main

then "apt-cache update; apt-get install lives" will install the application and it's pre-requisites.

and you are set in terms of video editing.
Next I want to make my apps look good I want mplayer to have a great looking gui so I go here
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

Scroll down till you get to skins download them all put all zip files into a disposable folder now install into mplayer skins folder located in usr/share/mplayer/skins just rightclick on each extract here and voila you have about 25 new skins to choose from. XMMS is even easier in your home directory go to view >show hidden files and see .xmms open and xmms skins folder is here just go to the xmms website download all the skins you want and cut and paste into that folder.

This should take less than 3 hours start to finish, you will be able to watch all media , you will have java and flash installed be able to play mp3's dvd's and do video editing.

I hope its of some help to anyone wanting to use Ubuntu breezy!!

---

### Post by irish rebel on 2005-12-02
and if anyone needs assistance setting up any other apps just reply to post and I will help as good as I can.

---

### Post by lysis on 2005-12-03
[QUOTE=irish rebel]and if anyone needs assistance setting up any other apps just reply to post and I will help as good as I can.[/QUOTE]
i'm STILL having problems with enemy-territory. i also need an audio editing program (similar to cubase or sonar)

i saw one in the OFFICIAL WINDOWS TO LINUX LIST but i didn't see it in apt-get and i'm unfamiliar with how to install it. (it wants jack, and i can't get it to work after installing jack.  it sucks :(  )

i got dvds, opera, and i think java and flash working.  the Music Player for myspace says it needs content; not sure what plugin i need there.

---

### Post by mrmcctt on 2005-12-03
> OH automatix, i'm not seeing where to actually download it. you link me all over the damn forums with that program, but nowhere i see a link to it's site or a link to get it. it's not in synaptic.

You can get Automatix [in this thread]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix").  Look at the bottom left corner of the very first post and you will see > File Type: gz
automatix-ubuntu_v3.4.5.tar.gz (22.9 KB, 3012 views)  I didn't put the download link here.  I think it's better that you go to the Automatix thread to download.  Instructions for use are there.  They are very straight forward and easy to follow.

Click on the link to download the file and follow the instructions in the very first post of the Automatix thread to install and use Automatix.

---

### Post by joshuapurcell on 2005-12-03
[QUOTE=lysis]OH automatix, i'm not seeing where to actually download it.  you link me all over the damn forums with that program, but nowhere i see a link to it's site or a link to get it.  it's not in synaptic.[/QUOTE]
First, use the link he gave in his initial post. Then read the first post in the thread that appears. It tells you exactly where to find Automatix (which happens to be from a link within that very post). Automatix is a script for automatically downloading and installing lots of good programs... which is why you won't find it in Synaptic.

---

### Post by irish rebel on 2005-12-03
One thing when I use automatix I do not install software thru it , I use synaptic for some reason using automatix gives me very unpredictable results, but since it changes your sources its able to use synaptic.
Sound problems with enemy territory mmm I have no clue I have unreal 2004 installed and it works fantastically on ubuntu[my sons pc] quake4 however gives sound problems but graphics work great.

---

### Post by lysis on 2005-12-03
sorry about the confusion; i tried taking the "OH i can't find it" out before anybody saw it.  i RTFM and found it myself. haha

it works for me and installed everything i selected. i ASSUME i don't need to reboot for anything (except numlock on) to take effect . . .

---

### Post by irish rebel on 2005-12-03
what I do when I install automatix is I click on the three items  one will set up synaptic other will set up the program and lastly one will set root password for you.
When I install nvidia driver I just search in syaptic for glx . Then for java I get sun java 1.5 .You can also get all the flash plugins ect . Every few weeks the sources change so you may have to reinstall automatix or google the latest repositories.

---

### Post by irish rebel on 2005-12-03
for audio editing go here search for plenty of software and if they dont have a deb package go to debian packages 
[http://www.linuxsoft.cz/en/sw_list.php?id_kategory=13](http://www.linuxsoft.cz/en/sw_list.php?id_kategory=13)

---

### Post by mckemie on 2005-12-07
I've been trying to use automatix.  With no success.  After I try to do something with automatix, I always end up with a "Setting up gstreamer0.8-----" sitting on my screen forever.  After I interrupt and try to "apt-get install" something, I am told to do a "dpkg --configure -a".  When I do so, I end up back at the infinite setting up of gstreamer.  Help?  How can I get out of the loop so I can at least use apt-get.

BTW, it looks like automatix has disappeared from the Ubuntu site.  Anyone know anything about that?

---

