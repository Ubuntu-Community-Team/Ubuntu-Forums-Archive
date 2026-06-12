---
title: "Assault cube"
date: 2011-11-20
forum: Gaming &amp; Leisure
---

### Post by raja.genupula on 2011-11-20
I wanna play that game so installed .

then here are the things giving me trouble.

1... for the first click it just open and its image displayed and automatically quit by its own and my screen will be zoomed automatically . then i have to open again to play . Then i can play that.

2...while playing that game at some point it will quit at some point .

3...after its quit my screen will be zoomed , to get normal screen again i have to logout and login 

this is the list of problems i am facing . so pleae help me to fix this things.

Thanks in advance.

---

### Post by raja.genupula on 2011-11-21
one more update i wanna add here
 
this game is good in my xubuntu 12.04 . I have this problem only in my Ubuntu 11.10.
 
But unfortunately my Xubuntu not booting now.
 
:( so i need a fix for this in My ubuntu 11.10 .
 
my system have 1366*766 or 8 monitor  and with 2 gb ram and 3.Ghz processor Intel Dual core system .
 
Already my firend joel helped me on this issue to play this by install mesa on my system , so game working but zooming after quit and automatic quit are the main issues now i am facing .
 
Thanks in advance .

---

### Post by Perfect Storm on 2011-11-21
Have you set the resolution ingame as the same your Desktop?

---

### Post by raja.genupula on 2011-11-21
Yeah yeah Joel suggest me how to do that and i set them as my desktop resolution .

---

### Post by raja.genupula on 2011-11-23
hey guys ....some one look at this please.

---

### Post by Perfect Storm on 2011-11-23
I can't help you further as I don't play that game, but is it the latest version of Assault Cube? You might check if there's a newer version which may deal with the problem you've experienced.


You can also check: [http://forum.cubers.net/forum-9.html](http://forum.cubers.net/forum-9.html)

---

### Post by Epinephrin3 on 2011-11-23
Did you install the additional libraries before you installed the game?  

From the assault cube site:

```
sudo apt-get install libsdl1.2debian-all libsdl-image1.2 libsdl-ttf2.0-0 libopenal1 
```

Have you tried running the game from the terminal to check for any errors that are output?

---

### Post by raja.genupula on 2011-11-24
Thank you both of you.  i will be back to you with results .

---

### Post by raja.genupula on 2011-11-24
> **Epinephrin3 said:**
> Did you install the additional libraries before you installed the game?  

From the assault cube site:

```
sudo apt-get install libsdl1.2debian-all libsdl-image1.2 libsdl-ttf2.0-0 libopenal1 
```

Have you tried running the game from the terminal to check for any errors that are output?

What you have suggested , is it trustable one  ? 

Why i am asking means because its uninstalled my ubuntu-desktop


```
assassin@assassin-ubuntu:~$ sudo apt-get install libsdl1.2debian-all libsdl-image1.2 libsdl-ttf2.0-0 libopenal1
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libopenal1 is already the newest version.
libopenal1 set to manually installed.
libsdl-image1.2 is already the newest version.
libsdl-image1.2 set to manually installed.
The following packages will be REMOVED:
  libsdl1.2debian-pulseaudio ubuntu-desktop
The following NEW packages will be installed:
  libsdl-ttf2.0-0 libsdl1.2debian-all
0 upgraded, 2 newly installed, 2 to remove and 52 not upgraded.
Need to get 226 kB of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libsdl1.2debian-all libsdl-ttf2.0-0
Install these packages without verification [y/N]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ oneiric/main libsdl1.2debian-all i386 1.2.14-6.1ubuntu4 [213 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ oneiric/universe libsdl-ttf2.0-0 i386 2.0.9-1build2 [13.0 kB]
Fetched 226 kB in 4s (53.4 kB/s)      
(Reading database ... 241016 files and directories currently installed.)
Removing ubuntu-desktop ...
dpkg: libsdl1.2debian-pulseaudio: dependency problems, but removing anyway as you requested:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.14-6.1ubuntu4) | libsdl1.2debian-all (= 1.2.14-6.1ubuntu4) | libsdl1.2debian-esd (= 1.2.14-6.1ubuntu4) | libsdl1.2debian-oss (= 1.2.14-6.1ubuntu4) | libsdl1.2debian-nas (= 1.2.14-6.1ubuntu4) | libsdl1.2debian-pulseaudio (= 1.2.14-6.1ubuntu4); however:
  Package libsdl1.2debian-alsa is not installed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is to be removed.
Removing libsdl1.2debian-pulseaudio ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
tar: ./shlibs: time stamp 2011-07-06 18:51:25 is 18623180.792194154 s in the future
tar: ./postinst: time stamp 2011-07-06 18:51:25 is 18623180.791643213 s in the future
tar: ./postrm: time stamp 2011-07-06 18:51:25 is 18623180.791388349 s in the future
tar: ./md5sums: time stamp 2011-07-06 18:51:43 is 18623198.791153997 s in the future
tar: ./control: time stamp 2011-07-06 18:51:33 is 18623188.790911156 s in the future
tar: .: time stamp 2011-07-06 18:51:43 is 18623198.790686361 s in the future
Selecting previously deselected package libsdl1.2debian-all.
(Reading database ... 241005 files and directories currently installed.)
Unpacking libsdl1.2debian-all (from .../libsdl1.2debian-all_1.2.14-6.1ubuntu4_i386.deb) ...
Setting up libsdl1.2debian-all (1.2.14-6.1ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
tar: ./shlibs: time stamp 2011-04-02 15:18:16 is 10402388.863734381 s in the future
tar: ./postinst: time stamp 2011-04-02 15:18:16 is 10402388.863233377 s in the future
tar: ./postrm: time stamp 2011-04-02 15:18:16 is 10402388.863008612 s in the future
tar: ./md5sums: time stamp 2011-04-02 15:18:20 is 10402392.862788715 s in the future
tar: ./control: time stamp 2011-04-02 15:18:20 is 10402392.862557125 s in the future
tar: .: time stamp 2011-04-02 15:18:20 is 10402392.862357359 s in the future
Selecting previously deselected package libsdl-ttf2.0-0.
(Reading database ... 241014 files and directories currently installed.)
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.9-1build2_i386.deb) ...
Setting up libsdl-ttf2.0-0 (2.0.9-1build2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

look at that

---

### Post by raja.genupula on 2011-11-24
man what you have suggested is very danger .
its deleted my Ubuntu-desktop .
again i have installed that but my unity top panel was gone .
unity --reset  

make everything fine to me.
please review once again before posting man .

---

### Post by Epinephrin3 on 2011-11-24
> **raja.genupula said:**
> man what you have suggested is very danger .
its deleted my Ubuntu-desktop .
again i have installed that but my unity top panel was gone .
unity --reset  

make everything fine to me.
please review once again before posting man .


Like I said I got that from the official assault cube website, you can have a look for yourself: [http://assault.cubers.net/download.html](http://assault.cubers.net/download.html)

And here for reference is exactly what it says;
> For installation guidence, read the [getting started]("http://assault.cubers.net/docs/getstarted.html") guide           in the AssaultCube documentation.         
          Linux users should take special note that they will need these additional libraries installed:         
         
[LIST]
[*]SDL 1.2
[*]SDL_image 1.2
[*]OpenAL Soft
[*]SDL_ttf 2.0
[/LIST]
                    If you're on a Debian or Ubuntu based system, you can run this command in a terminal to install these libraries:           
                       sudo apt-get install libsdl1.2debian-all libsdl-image1.2 libsdl-ttf2.0-0 libopenal1           
I am sorry that It did this to your install but I would have thought the people who make the game itself would be a pretty reliable source. Maybe they should be informed that what they suggest can be very dangerous on an Ubuntu install such as yours which looks to be 11.10 ?

---

### Post by raja.genupula on 2011-11-24
Its ok man . cool .

its just gave me like that , i am shocked for such kind of action . what ever my system is back to fine now man . 

so i think i am done with this , ok let it go like this,

Thanks to both of you .

---

### Post by Epinephrin3 on 2011-11-24
> **raja.genupula said:**
> Its ok man . cool .

its just gave me like that , i am shocked for such kind of action . what ever my system is back to fine now man . 

so i think i am done with this , ok let it go like this,

Thanks to both of you .

No problem bud. There is one site you could maybe use in the future though, playdeb.net. its a very well known reputable site and have even been included in the Ubuntu repositories list in the past. I have installed a lot of games through that site myself and all have worked 100% without problems.

About Ubuntu removing the desktop though I think this seriously needs to be looked at. I've tried myself to remove the gwibber app on 11.10 and synaptic also requested to remove the ubuntu desktop which got me confused... I also know someone who tried to remove other packages in 11.10 which are not required for the Ubuntu to work and have had the same problem.

What's going on with this? Its a bit ridiculous when people cant remove software they don't want on their own system. this sort of rubbish reminds me of windows!

---

### Post by raja.genupula on 2011-11-24
I think there may be a thread link , something like common file or something .

---

### Post by angryfirelord on 2011-11-24
For an 11.10 install, don't use that "all" package because that's what's causing the removal of the unity desktop. You actually only need 2 packages to get it going.
```
sudo apt-get install libsdl-image1.2 libopenal1
```
From there, I usually open up a terminal, cd into the directory and then run:
```
sh assaultcube.sh
```

---

### Post by raja.genupula on 2011-11-25
hmm it says those are already installed 

assassin@assassin-ubuntu:~$ sudo apt-get install libsdl-image1.2 libopenal1
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libopenal1 is already the newest version.
libsdl-image1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
assassin@assassin-ubuntu:~$ 


but issue **remains same**.


Thanks   for reply .

---

### Post by geronl on 2012-09-19
> **angryfirelord said:**
> For an 11.10 install, don't use that "all" package because that's what's causing the removal of the unity desktop. You actually only need 2 packages to get it going.
```
sudo apt-get install libsdl-image1.2 libopenal1
```From there, I usually open up a terminal, cd into the directory and then run:
```
sh assaultcube.sh
```


first one already installed

second one - can't open assault cube

---

