---
title: "[Easy Installation Script]  Secret Maryo Chronicles"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-07-08
=====================================================
[Easy Installation Script]  Secret Maryo Chronicles
[http://www.secretmaryo.org/index.php?page=public_news](http://www.secretmaryo.org/index.php?page=public_news)
Screenshots:[http://www.secretmaryo.org/index.php?page=media](http://www.secretmaryo.org/index.php?page=media)
=====================================================
    
   
(I could read users with troubles to play this game)
  
The 5 lines code to install the game:
```

sudo su
cd /root
wget -N http://patrick295767.sitesled.com/easyscripts_installers/easy_smc_patrick_install.sh
sh easy_smc_patrick_install.sh
exit

```
([code]("http://patrick295767.sitesled.com/easyscripts_installers/easy_smc_patrick_install.sh"))

to run the game, just type into the console : 
  
smc 
or 
smc.x

Enjoy !!
  
====
If you'd like sound & music; this script can do it:
```
sudo su
cd /root
wget -N http://patrick295767.sitesled.com/easyscripts_installers/easy_smc_patrick_music_install.sh
sh easy_smc_patrick_music_install.sh
exit
```
  
  
==========
> **fakie_flip said:**
> The link is down. I can't get the script. Has anyone tested the script in Feisty?
  
I do not have ubuntu anymore. To install:
  
1/ ubuntu way:
[http://www.secretmaryo.org/index.php?page=game_downloads&sid=sid=1b93f7130f0f9679cafc2e4cc10f4479](http://www.secretmaryo.org/index.php?page=game_downloads&sid=sid=1b93f7130f0f9679cafc2e4cc10f4479)


2/ 
very easy way, Debian:
[http://ftp.de.debian.org/debian/pool/main/s/smc/smc_1.0-1_i386.deb](http://ftp.de.debian.org/debian/pool/main/s/smc/smc_1.0-1_i386.deb)
dpkg -i smc_1.0-1_i386.deb

---

### Post by vem0m on 2006-07-09
Great Work! i tried and tried to get this going i got all the deps(i thought) and everything searched and searched for something to ehlp this worked and game runs thx so much :D

---

### Post by oczindian03 on 2006-07-11
I'm sorry if i sound dumb but i'm newer to Linux and i downloaded smc. It is now on my computer but when i double click it nothing happens. Could you help me? If you want you can pm me.

---

### Post by vem0m on 2006-07-11
hmmmm how did u install it? using this guide? if not try using this guide it will make ur icons ETC and u will be up and running in less then 10 min :)

---

### Post by oczindian03 on 2006-07-11
I just opened the terminal copied the 5 lines and it installed by it self. After that i went to games clicked smc w/the little mario pic but it was non-responsive.

What does it mean type smc into the console? What and where is the console?

---

### Post by slugkilla on 2006-07-11
Awesome man. I tryed to get this game running last week but it did not work. You have a way with scripts. Great job.

P.S- oczindian03- Just use the Terminal/commandline like you used to install, and type 
```
smc.x
```
just like that.

---

### Post by oczindian03 on 2006-07-11
> **slugkilla said:**
> Awesome man. I tryed to get this game running last week but it did not work. You have a way with scripts. Great job.

P.S- oczindian03- Just use the Terminal/commandline like you used to install, and type 
```
smc.x
```
just like that.

Okay i did that and heres the response i get...

./smc: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
alex@alex-desktop:~$

what now?

---

### Post by vem0m on 2006-07-11
u are missing a dependcy go back to terminal/console and type
```
 sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev
```

---

### Post by oczindian03 on 2006-07-11
alright i did that. now what do i do?

---

### Post by slugkilla on 2006-07-11
did ya try running smc.x again?

---

### Post by oczindian03 on 2006-07-11
Here's what i get when i do.

alex@alex-desktop:~$ _**smc.x**_
./smc: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by vem0m on 2006-07-11
ok now u are missing another set go back to terminal/console and type:
```
sudo apt-get install libsdl-mixer1.2 libsdl-mixer1.2-dev
```
and try running  smc.x again

---

### Post by oczindian03 on 2006-07-11
WOW Thanks A LOT! Was this my fault or the scripts? Because i did the script twice to see if it would find the stuff i'm missing and apparently it didn't.
Well now it works! Thanks again to all that helped.:D

---

### Post by vem0m on 2006-07-11
no problem dude its the scripts i believe as i don't think it installs all the dependencies i had tried to compile from source b4 i came across this script so i had already d/led the deps but glad to see its working :) HAVE FUN!

---

### Post by mhancoc7 on 2006-07-11
Awesome!!! I am so excited. 

It is working perfect for me except for the music. I get the sounds, but no music. 

Thanks so much, Jereme

---

### Post by oczindian03 on 2006-07-11
Okay another question for future reference how do i uninstall it? I went to add/remove programs but its not there. i even searched it... nothin.

---

### Post by charles.regan on 2006-07-11
smc: error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: No such file or directory

so I did: sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev   

The following packages have unmet dependencies:
  libsdl-ttf2.0-dev: Depends: libsdl1.2-dev (>= 1.2.4) but it is not going to be installed
E: Broken packages


Why ?? How can I fix this ?

---

### Post by vem0m on 2006-07-11
hehe ok now hld on
```
 sudo apt-get install libsdl1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl-mixer1.2 libsdl-mixer1.2-dev
```

try that :)

---

### Post by patrick295767 on 2006-07-12
> **mhancoc7 said:**
> Awesome!!! I am so excited. 

It is working perfect for me except for the music. I get the sounds, but no music. 

Thanks so much, Jereme
  
And this :
```
sudo su
cd /root
wget -N http://patrick295767.sitesled.com/easyscripts_installers/easy_smc_patrick_music_install.sh
sh easy_smc_patrick_music_install.sh
exit
```
Should give you the music. 
  Is there an error message ? Normally, It should work great.

---

### Post by mhancoc7 on 2006-07-12
Ok, I tryed the script again and I noticed that the last line of the terminal output said "cp omitting data" or something like that. I decided to try and download the music file from the SMC homepage and install it manually. I copied the data folder from the music download into my SMC folder and selected yes to replace. Now I have music!!

Thanks again for the script.

Jereme

---

### Post by mhancoc7 on 2006-07-12
Hi, I noticed that I had one other issue. After I select "Start" I have a red outline of Maryo on the map. I finally decided to see if I could fix it. So I downloaded the Windows version and installed it to my Windoze XP (Vmware) and located the Maryo graphics that were missing. I had to rename them and copy them to the appropriate folder but now I have Maryo on the map. If anyone else has the same issue here is how to fix it.

* Download the attachment below.
* Extract it to your Desktop.
* copy the "maryo" folder into /usr/local/games/SMC/data/pixmaps/world/
* You will need to do this as root. If asked if you want to replace say yes.

That's it now you have the proper graphics.

Jereme

---

### Post by charles.regan on 2006-07-12
rrrrrrrrrg!!!!!!!!!!!!!!!!
Do you think my sources.list is doing this all this crap?!?


admin@Pizzabob:~$  sudo apt-get install libsdl1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl-mixer1.2 libsdl-mixer1.2-dev
Password:
Reading package lists... Done
Building dependency tree... Done
libsdl-ttf2.0-0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages
admin@Pizzabob:~$


So I did this after:


admin@Pizzabob:~$ sudo apt-get install libartsc0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libartsc0 (= 1.5.2-0ubuntu1) but 1.5.3-0ubuntu0.1 is to be installed
E: Broken packages


Why why why...

---

### Post by vem0m on 2006-07-12
just install and add to the install string till all deps are met lol

---

### Post by clarego on 2006-08-29
finally got the game to work thanks pat!!!

---

### Post by guine on 2006-08-29
After playing for a little Ive run into a couple of problems.
1.  I tried the thing to get music working but I still dont have any music except when I complete a level.
2.  The save option in the menu isnt working and I was wondering if there are save places in the game that do work or am i supposed to be able save from the menu when i pause the game.
3.  Has anyone else been having any problems with getting stuck in the ground, air, or enemies?

---

### Post by yodaky on 2006-08-29
I have installed the game exactly as described in the first post; however, when I try smc and smc.x it says 'command not found'.

---

### Post by kinkdxm on 2006-12-15
edit:
fixed my own problem by reading the previous posts more carefully
:)

---

### Post by amunimanghi on 2006-12-16
Wow, this is nice. I could never get it to work either. I can't get passed the first level. =-= stupid goombas and their super touching powers to kill you. :p

---

### Post by geek_Man on 2006-12-22
I was trying to install SMC and since I don't have a clue how to compile stuff, I downloaded the precompiled package, but couldn't get that to work. Tried the script and it worked! Great job!

---

### Post by Odisej on 2006-12-30
Well, it says command not found. Can somebody help.. Using edgy.

Thanx,

Odisej

---

### Post by tastefulasever on 2007-04-01
does anyone have this script still?

---

### Post by fakie_flip on 2007-04-22
The link is down. I can't get the script. Has anyone tested the script in Feisty?

---

### Post by patrick295767 on 2007-08-06
> **fakie_flip said:**
> The link is down. I can't get the script. Has anyone tested the script in Feisty?
  
I do not have ubuntu anymore:
  
1/ ubuntu way:
[http://www.secretmaryo.org/index.php?page=game_downloads&sid=sid=1b93f7130f0f9679cafc2e4cc10f4479](http://www.secretmaryo.org/index.php?page=game_downloads&sid=sid=1b93f7130f0f9679cafc2e4cc10f4479)


2/ 
very easy way, Debian:
[http://ftp.de.debian.org/debian/pool/main/s/smc/smc_1.0-1_i386.deb](http://ftp.de.debian.org/debian/pool/main/s/smc/smc_1.0-1_i386.deb)
dpkg -i smc_1.0-1_i386.deb

---

### Post by rcatman on 2007-09-07
The only problem I had was installing the music. I finally found where the smc directory is. Copy the music folder to /usr/share/games/smc

---

