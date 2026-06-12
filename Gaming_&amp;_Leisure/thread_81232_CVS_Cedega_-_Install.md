---
title: "CVS Cedega - Install"
date: 2005-10-24
forum: Gaming &amp; Leisure
---

### Post by Tatah on 2005-10-24
Please, how I install CVS Cedega in Breezy???
Step by step!!!
Thanks!!!

Tatah

---

### Post by seethru on 2005-10-24
[QUOTE=Tatah]Please, how I install CVS Cedega in Breezy???
Step by step!!!
Thanks!!!

Tatah[/QUOTE]
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45")

---

### Post by Tatah on 2005-10-24
[QUOTE=seethru][http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45")[/QUOTE]

I´ve tested this tutorial, but, does´nt work!!!
Error in Make, like everyone!!!

Help please!!! I need to play CSS!!!

Thanks

Tatah

---

### Post by arcanistherogue on 2005-10-24
I just payed the money.  Rather not have to fiddle with it too much to get my games working, I just want to play them.

---

### Post by Curlydave on 2005-10-24
[QUOTE=Tatah]I´ve tested this tutorial, but, does´nt work!!!
Error in Make, like everyone!!!

Help please!!! I need to play CSS!!!

Thanks

Tatah[/QUOTE]

It doesn't work for anyone, and the forum mods over at linux gamers don't have an answer other than "you didn't follow the tutorial right", which is not sufficient or correct. There is no answer yet.

---

### Post by seethru on 2005-10-24
If you want my opinion, do what I did and just pay the money. It's worth it, especially with cedega 5.0 coming soon.

---

### Post by RAOF on 2005-10-25
At least one problem is that gcc-4 will fail to compile cedega.  You can **try** doing this:
```
sudo apt-get install gcc-3.4
CC=gcc-3.4
export CC
./WineCVS.sh

```
I can't verify that it works, 'cause of a problem with compiling 32bit code on Breezy64, but I think that that should allow you to install cedega.

---

### Post by Tatah on 2005-10-26
Doesn't work!!!

I need CVS Cedega!!!
Help Please!!!

---

### Post by orgy on 2005-10-26
i need help with CVS Cedega too, im having the same error every1 has.
And i dont wanna pay for Cedega 'cause i dont know if its going to work, i know theres a list of the compatible games but still i dont wanna play CSS and get low Frame per Second.

---

### Post by Tatah on 2005-10-26
Me too!!!
Wine can run CSS???

---

### Post by seethru on 2005-10-26
I play CS:S using Cedega, and it's smooth. Post your system specs and I'll be able to tell you if it's worth your trouble.

---

### Post by Tatah on 2005-10-26
Sempron 2800
Ati 9600
512 ram
a7n8x-e deluxe
ubuntu 5.10

---

### Post by ltmon on 2005-11-05
Hi...
To compile Cedega under breezy you can't use GCC 4.

Unfortunately the makefiles for Cedega don't use the "CC" environment variable (*bad people*), so that's why the solution above didn't work.

So I did this:

sudo unlink /usr/bin/gcc
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc

(now do the compile of cedega)

sudo unlink /usr/bin/gcc
sudo ln-sf /usr/bin/gcc-4.0 /usr/bin/gcc

That should work.

L.

EDIT: OK it seems this does actually get cvscedega compiled fine, but it segfaults every time I try to run even the simplest .exe.  Anyone know how to get this running on Breezy??

---

### Post by Biased turkey on 2005-11-05
cedega isn't worth the 5$ a month.
I've been subscribing for 6 months and **none of the games I own is working** :
CMR rally, RBR rally,Racing legends, F1 challenge, Panzer general scorched3D, even UT sucks ( UT linux native version works nicely both with an ATI9600 and Nvidia 6600 ) 
cedaga is just a crappy plaster on a wooden leg.

---

### Post by slimb on 2005-11-07
[QUOTE=Biased turkey]cedega isn't worth the 5$ a month.
I've been subscribing for 6 months and **none of the games I own is working** :
CMR rally, RBR rally,Racing legends, F1 challenge, Panzer general scorched3D, even UT sucks ( UT linux native version works nicely both with an ATI9600 and Nvidia 6600 ) 
cedaga is just a crappy plaster on a wooden leg.[/QUOTE]

in my experience, its more than worth the 5 bucks a month considering I can play the games listed below at a more than acceptable level (in most cases i can have my video settings just a notch under what i run on the windows box) : city of heroes, WOW, War3, neverwinter nights (although the linux client is available and runs better), EQ and EQ2, and finally guild wars.

YMMV.

---

### Post by hndrcks on 2005-11-17
[QUOTE=slimb] EQ ***and EQ2***[/QUOTE]

You have EQ2 running in Cedega?

---

### Post by Josef K. on 2005-11-20
[QUOTE=ltmon]Hi...
sudo unlink /usr/bin/gcc
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
(now do the compile of cedega)
sudo unlink /usr/bin/gcc
sudo ln-sf /usr/bin/gcc-4.0 /usr/bin/gcc
That should work.
[/QUOTE]

yes: this let you pass gcc error, but
how did you manage libwine_unicode.so up to date error?!
even if I've installed libwine-dev I get this error :confused:

---

### Post by rogeriovinhal on 2005-12-21
I have just installed, and got this message:

```
Installing launcher script ...
    Packing sourcetree...
All done ... CVS installed

   Installed as: cvscedega
   Config path : <homedir>/.cvscedega

```

But when I try to run "cvscedega" there's no file found, if I do "whereis cvscedega" nothing appears, and if I try to go into "~/.cvscedega" that directory doesn't exist.

Where did it install anyway?

---

### Post by Perfect Storm on 2005-12-21
[QUOTE=Biased turkey]cedega isn't worth the 5$ a month.
I've been subscribing for 6 months and **none of the games I own is working** :
CMR rally, RBR rally,Racing legends, F1 challenge, Panzer general scorched3D, even UT sucks ( UT linux native version works nicely both with an ATI9600 and Nvidia 6600 ) 
cedaga is just a crappy plaster on a wooden leg.[/QUOTE]

I agree with Slimb. I got a dozen games working with Cedega pay version. Did you check the rating list on these games on transgaming.com before paying for Cedega?
By the way Scorched3D have a linux Client.

---

### Post by christooss on 2006-01-16
[QUOTE=rogeriovinhal]I have just installed, and got this message:

```
Installing launcher script ...
    Packing sourcetree...
All done ... CVS installed

   Installed as: cvscedega
   Config path : <homedir>/.cvscedega

```

But when I try to run "cvscedega" there's no file found, if I do "whereis cvscedega" nothing appears, and if I try to go into "~/.cvscedega" that directory doesn't exist.

Where did it install anyway?[/QUOTE]

Ive got the same problem. Does anybody have a solution

---

### Post by handy on 2006-01-16
You are on 32bit Breezy?

---

### Post by MacV on 2006-01-17
[QUOTE=christooss]Ive got the same problem. Does anybody have a solution[/QUOTE]

Try re-installing it.

---

### Post by handy on 2006-01-17
I installed a few days ago, following the this howto:

[http://doc.gwos.org/index.php/CedegaCVSInstallation](http://doc.gwos.org/index.php/CedegaCVSInstallation)

I had one problem & that was an oversight on my behalf, once corrected It installed with no complaints.

I've found:   **$/home/handy/.cvscedega/**

Contents follow:

[HTML]handy@BirdFish:~$ cd /home/handy/.cvscedega
handy@BirdFish:~/.cvscedega$ ls
config   drive_c     reglog      userdef.reg  wineserver-BirdFish
config~  oldreg.md5  system.reg  user.reg
handy@BirdFish:~/.cvscedega$[/HTML]

Does that look correct?

I tried 2 games that probably don't work on cedega anyway, so I don't know if it works?

The games that I tried were **Carmageddon** & **GP4** ?

**[EDIT:]  *To the best of my knowledge, the above 2 games have not been successfully run by anyone under Wine, CVS Cedega, commercial Cedega or dosboxer!***

Any feed back is much appreciated,

Thankyou...

---

### Post by christooss on 2006-01-19
yes im on 32 bit breezy.

I found a bin dir in my home dir. It includes cvscedega. Wierd.

---

### Post by jon_z on 2006-01-20
Has anyone else tried using [this]("http://doc.gwos.org/index.php/CedegaCVSInstallation") link to install CVS Cedega? I have wine 0.9.3 setup properly to allow me to use Steam, so im not in the mood to risk breaking anything...

---

### Post by dezgot on 2006-03-07
I have the same missing cvscedega thing, even after reinstalling a few times.  My solution is to reboot into windows... :cry:

And yes, everyone has used [http://doc.gwos.org/index.php/CedegaCVSInstallation](http://doc.gwos.org/index.php/CedegaCVSInstallation), it's just an archive of the howto on linuX-gamers.net.

---

### Post by christooss on 2006-03-07
there is a bin dir in your home dir. And there you go you have cvscedega in it.

Majbe it would help if ./configure would be run with usr/share prefix. Or something like that. Maybe others would say how this is properly done.

---

### Post by derekd on 2006-03-07
Need help installing Cedega 5.1, can someone help?

---

### Post by handy on 2006-03-26
People don't ***seem*** to have much success with the cvs cedega.

I have been using commercial cedega now for nearly 2 months.

***Commercial cedega, is NOT the same software as the cvs cedega!!***

I only use it to play **Guild Wars**, & Cedega 4.4.3, is the version of choice for **GW**.  I am much happier playing **GW**, than wasting a lot of time messing around trying to get it to work under Wine (won't run) or cvs Cedega, where **GW** will almost run...:( 

***[Follow this link if you are interested in GW & Cedega:]("http://ubuntuforums.org/showthread.php?t=123715")***

As I state in that thread, I am so glad that I coughed up, for the minimum sub' of $15 US.  If I hadn't I'd still have to play **GW** on windoze...:rolleyes:

---

### Post by jeffreyvergara.NET on 2006-06-10
I'm having problem compiling the latest Cedega CVS, i got this error:
> 
ffmpeg/libavcodec/h263.c:1744: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [ffmpeg/libavcodec/h263.o] Error 1
make[2]: Leaving directory `/home/jeffrey/winex/dlls/quartz'
make[1]: *** [quartz/libquartz.so] Error 2
make[1]: Leaving directory `/home/jeffrey/winex/dlls'
make: *** [dlls] Error 2

---

### Post by jeffreyvergara.NET on 2006-06-10
ok it's fixed... my mistake... i did not use gcc-3.4

---

### Post by patrick295767 on 2006-06-10
(I made a script to help cvs cedega install : [http://www.ubuntuforums.org/showthread.php?t=193814](http://www.ubuntuforums.org/showthread.php?t=193814))
I hope that ll help a bit.
  
Greetings

---

### Post by thunderduck3141 on 2006-07-17
wine can run a LOT more games that cedega

---

