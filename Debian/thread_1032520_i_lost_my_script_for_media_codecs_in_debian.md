---
title: "i lost my script for media codecs in debian ???"
date: 2009-01-06
forum: Debian
---

### Post by cmay on 2009-01-06
hi.
i have used debian since sarge. the last two month of sarge anyway. i had a script for installing the restricted codecs in debian which i had on a usb stick and almost never used and i have lost the usb stick content all togheter. i normally do not install flash or restricted stuff on debian but as it just so happens i just got a hauppage wintv card which i would like to see if i can have working on debian. it works on myth ubuntu but i miss etch. can anyone remember how the restricted multimedia stuff is installed on debian. i did it once using a script i must have stolen of the internet somewhere ? . 
thanks for the time.

---

### Post by oswaldkelso on 2009-01-06
Do a search here for hauppage, you didn't say if your card was pvr hvr or usb 
[http://forums.debian.net/search.php](http://forums.debian.net/search.php)

also see here [http://www.linuxtv.org/](http://www.linuxtv.org/)

and debending on your kernel here

[http://www.isely.net/pvrusb2/pvrusb2.html](http://www.isely.net/pvrusb2/pvrusb2.html)

to identify 
~dmesg
[74771.477191] usb 5-4.1: Product: WinTV HVR-900
or
[http://www.hauppauge.com/site/products/data_hvr950mac.html](http://www.hauppauge.com/site/products/data_hvr950mac.html)

---

### Post by cmay on 2009-01-06
thanks. the card is a dvb -t  standard pci card.  its called exactly a "hauppage wintv nova -t "and it works out of the box with eARos and myth buntu. but i wanted to see if i could get it to work on debian as well. since i am a debian user mostly . thanks a lot for the links. i will do some reading on them later on tonight .

---

### Post by oOarthurOo on 2009-01-08
Seen this?

[http://debian-multimedia.org/](http://debian-multimedia.org/)

---

### Post by wolfen69 on 2009-01-09
when i had debian, to get my hauppauge pvr150 working i had to install the ivtv modules. i installed module-assistant then did ```
m-a a-i ivtv
``` and i also installed the ivtv firmware from synaptic. then finished it with ```
rmmod ivtv && modprobe ivtv
```

but i'm guessing you will need v4l drivers and not ivtv. but you might be able to take the same approach.

---

### Post by cmay on 2009-01-09
> 
**Re: i lost my script for media codecs in debian ???**
 		Seen this?

[http://debian-multimedia.org/](http://debian-multimedia.org/)
no i did not see this before ,but thanks a lot. 
i have tried to install tvcard in my older comp but it simply is too low on specs so i decided to plug it into my new computer and i have tried to get it workin but the problem that arises is that when i installed etch the is no screen (devises ) found in /etc/X11/xorg.conf  and i am placed in a shell enviroment instead of a nice gnome desktop. i was working on it late at night last night so i did not make it work yet. i reinstalled ubuntu and installed elisia mediacenter to see if the card works which it does. so now i want to try to get a working debian install out of it if possible. it should be a debian since i think i can maybe use the base installer cd to get only the minimal amount of programs i need once i found out exactly how it should be setup. i have a new nvidia card which could be the couse of the debian install failing. the first system ever installed on computer was  etch since i got it with out any operative system installede.  
[]("http://debian-multimedia.org/")

---

### Post by cmay on 2009-01-13
ok i found something i wrote for my brother once. but the multimedia stuff keyring do not install from commandline for some reason. i once had a working script i got somewhere from . i guess its a link to a how to for the exact same multimedia page as i been directed to here. this is a older beginning using linux   how to/should do i wrote for my self and my brohter. (just in case he would see the light and completly switch to linux) anyone knows why it cant apt get the keyring. the actual script i had was figuring out if the debian was etch lenny on i386 or a amd64. i cant even remember where i got it from. i am trying to build a multimedia production and mediacenter out of etch since the 64studio distro is very nice but i just want to be able to do it from a standard etch install so i can have my own debian like i want it instead of using different distros for all sorts of things. 
[PHP]HOW TO to get dvd playback on debian etch
 
please make sure to edit the sources list first 
the proper resporitorie will most be
deb http://www.debian-multimedia.org etch main
  
sudo gedit /etc/apt/sources.list
or nano /etc/apt/sources.list

add the deb http://www.debian-multimedia.org etch main so the resporitories are enabled. 
then run 

sudo wget http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2008.10.16_all.deb
#
then run 
#
sudo dpkg -i debian-multimedia-keyring_2008.10.16.deb
#
or from apt-get run 
sudo apt-get debian-multimedia-keyring_2008.10.16_all.deb

then run the simple commands that allows the magic to happen
i would prefere to do it all in a script (with all my favorite programs added )
just find the packages you want and write like this sceleton script 
and then save as media-install in homefolder . do a chmod 755 ./media-install and run it by the terminal ./media-install and it should if all resporitories are correct set up just install dvd playback and flash or what ever you added. enjoy

# MAGIC (sceleton) SHELLSCRIPT TO GET DVDPLAYBACK IN DEBIAN
#! /bin/bash
sudo apt-get update
sudo apt-get install w32codecs libdvdcss2
sudo apt-get upgrade[/PHP]

---

### Post by oswaldkelso on 2009-01-14
#nano /etc/apt/sources.list

add

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main 

to the list changing etch to main, or lenny or testing depending on what you run

save it.



# apt-cache search keyring
debian-multimedia-keyring - GnuPG archive key of the debian-multimedia repository
etc.....
# apt-get install debian-multimedia-keyring

Then add what ever software you need. I've never had to install w32codecs specifically.

---

### Post by cmay on 2009-01-15
gahhh ,of course .
thanks.
i have my operated so i cant see these things so good anymore. i but fixed it. 
thanks a lot for the help :)

---

### Post by polmir on 2009-01-20
Add backports in /etc/apt/sources.list:```
deb http://www.backports.org/debian etch-backports main contrib non-free
```

[http://www.backports.org/dokuwiki/doku.php]("http://www.backports.org/dokuwiki/doku.php")

---

### Post by cmay on 2009-01-20
thanks. after i got my eyes operated i cant see these things so good anymore. but i have upgraded to lenny using the xfce + lxde cd image on one of my oldest computers . i can tell you that on a computer with the specs 600 mzh and 300 mb ram it can show movies just great. so when i am done making my media center with the tv card and are ready to install debian i will use this cd image. i have orded a new case for the computer setup so its a real media center. it takes a while for it to come so i just "practise" setting up some media stuff on my older computer. 
thanks for the time.

---

### Post by polmir on 2009-01-20
For older computer try this:
[http://geexbox.org/en/index.html]("http://geexbox.org/en/index.html")

---

### Post by cmay on 2009-01-21
i already tried that. sorry to say it is still not stable enough(yet) . but i got this media-center package from here [http://www.linuxpusher.com/index.php?cPath=106_108&osCsid=e44d8625261cc9657978ff11b9ae7bdd](http://www.linuxpusher.com/index.php?cPath=106_108&osCsid=e44d8625261cc9657978ff11b9ae7bdd) which i am planning to learn to fix older computers if possible so people dont trash them and make linux based media centers instead. the one media center i have made is using crunch bang linux i have the hauppage tv card in it as for now. but i have orded a rack mountable case which can be built into my rack for my audio studio. and i plan to build it from base up with both my tv tiuner card and my emu 1212m soundcard using debian lenny when the case comes. i was disapointed at the new release of 64tudio which i been a happy user of since i read about it some years ago. so its time to learn how to make a debian based multimedia and audi production enviroment from scratch. i installed ubunt studio last night in my computer i  use for audio recording to see if it is any better. if not i could upgrade to jaunty and run some betatesting until i get my new case and my audio studio fixed. i also really would like to make home made music videos so i think that tv card with remote could belong in the audio production enviroment as well. thanks for the time.

---

