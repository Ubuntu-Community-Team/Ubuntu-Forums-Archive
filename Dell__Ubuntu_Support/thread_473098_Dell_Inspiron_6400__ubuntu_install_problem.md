---
title: "Dell Inspiron 6400 / ubuntu install problem"
date: 2007-06-13
forum: Dell  Ubuntu Support
---

### Post by monkey1977 on 2007-06-13
Well, after thinking about it for ages i decided to back up everything on my laptop and make the jump from windows to linux, and before i even have a chance to sample the brave new world my new installation won't even load.....

Firstly, I have an Inspiron 6400 with Intel Dual Core, 1GB Ram, Ati Radeon x1400 256mb ram (15.4" widescreen display), intel pro wireless adapter....

and have tried to install ubuntu 7.04 alternate i386....

i initially downloaded the other version (not the alternate one) but i couldnt even install it, so tried the above mentioned version instead. got an error message about not being able to start x server (my graphical interface - apparently!)

when deciding to install  linux I opted to wipe my laptop completely rather than have seperate partions ( i have second laptop running windows for backup so its no big issue that the installation of ubuntu is working just yet!)

I sucessfully managed to navigate the installation process and held my breath and waited to be greeted by my lovely new linux operating system, but after the dell "splash" screen all i get is a black screen and nothing else happens.......

i think i have also tried to load via a kinda "safe mode" thing (by pressing escape upon boot up, but i get an error message similar to this:

"could not start x server" (your graphical interface).... i am then given the option to study a log of some kind, followed by another one but it all means nothing to me as i am a total newb....(im sure it shows) .i presume that this is what is causing my screen to go black when i try to boot up ubuntu?

can anyone shed any light on the problem my installation is having? 

if any suggestions are forthcoming, could anyone please assume i am an idiot as i know nothing about what i am doing here! anything i have ever installed in the past has been done so by an included installer so my knowledge of such things is ZERO!

Thanks for anyone kind enough to spend a moment to read my text, i hope to be up and running soon with the help of you good people!

I hope i have included enough information, if not, please let me know!

thanks

neil

---

### Post by damn66 on 2007-06-13
u need this..gnome would be a good start ;)
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x11-wm.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x11-wm.html)

---

### Post by The Groovy Guru on 2007-06-14
Hi Monkey

I have a 6400 which I installed Feisty on when it came out. The good news is I had the same problem. The bad news is I forget all the details

Anyway I installed with the standard disk. Put that in as you did and when it complains about not starting the xserver it should take you to a command prompt. If it doesn't hit ctrl-alt-F1 and you'll be at one.

Now the problem is the screen resolution. I have a 1680x1050 screen. Anyway I recall that 1280 x 1024 will do the job. 

Now at the command prompt run the command

sudo dpkg-reconfigure xserver-xorg

This will run through some rigmarole which you can just except the defaults for except for two things. When it wants the vide driver pick "vesa" I think (bit rusty on that, sorry), second when it asks what res pick 1280x1024.

Now at the command line run

sudo /etc/init.d/gdm start


That should get the live CD fired up with the wrong screen res. Install the restricted video driver (it will be obvious how to do that) and then it should fix the screen res up. Now you can install.

Good luck ;)

---

### Post by jhollett66 on 2007-06-14
Try this it worked for me
[http://www.ubuntugeek.com/howto-install-feisty-beryl-on-dell-inspiron-6400-ati-x1400-dell-1390-wifi.html](http://www.ubuntugeek.com/howto-install-feisty-beryl-on-dell-inspiron-6400-ati-x1400-dell-1390-wifi.html)

Good luck

---

### Post by smitty2point0 on 2007-06-15
I did the same....just followed the directions on the thread posted about....fiesty fawn with beryl working like a champ...seems to be running a little hot...but oh well.

---

### Post by neptho on 2007-06-15
> **smitty2point0 said:**
> I did the same....just followed the directions on the thread posted about....fiesty fawn with beryl working like a champ...seems to be running a little hot...but oh well.

Update your BIOS to A15.  It fixed my overheating problems.

---

### Post by vco08 on 2007-06-16
Weird. ive got the 6400 and had no problems what so ever when installing Kubuntu 7.04. In fact, it installed quite nicely and fast.

---

### Post by deadspeak on 2007-07-10
i'm having the exact same problem, tried both suggested methods to resolve it but still not letting start up x,
it just says GDM startup [Failed]
don't konw what to try next.......

---

### Post by bdavies on 2007-07-10
i am also having this problem and have tried everything everyone has said

---

### Post by Paul S on 2007-07-10
It would help us to troubleshoot if you posted your xorg.conf files and let us know what video card you have.  The 6400 can come with nvidia, ati, or intel (and each works differently).

---

### Post by RangerDanger on 2007-07-10
Here, look at my thread from a few days ago, the advice really worked.  You just need to be plugged into a wired connection.  I followed exactly what I was told by the second poster an was up and running in no time flat.

[http://ubuntuforums.org/showthread.php?t=488999](http://ubuntuforums.org/showthread.php?t=488999)

---

### Post by elixirofLIFE on 2007-07-11
I got exactly the same trouble :). Hope I can get some advice from this Threads :). 
Well, My Dell is Inspiron 6400 with Intel Dual Core, 2GB Ram, Ati Mobility Radeon x1400 128mb ram (15.4" widescreen display), intel pro wireless adapter....
I can install Ubuntu 6.10 but Got the same pros with Ubuntu 7.04. 
It is not a big deal though. But I think the graphic of Ubuntu 7.04 is cooler???
Anyway, I can't install Xubuntu 7.10 as well with the same error message replied. 
Kubuntu is somehow I could not try since I cant even install, probably the disc is defective.

---

### Post by batteries2857 on 2007-11-11
Hello, I downloaded Simply Mepis It recognized every thing right away and doesn't run hot. My Ubuntu had the same problem as everyone else so I gave up. I'm not very computor savey so unless it's easy I give up. BUT it didinstall on my desktop very easy and no problems

---

### Post by batteries2857 on 2007-11-11
Hello once again. Ubuntu is a nice OS but needs to be developed so that it recognizes any stystem that it is installed in. Noticed that Xandros has a new system that does just that.
 It also has Crossover Office and Code weavers crossover so that you can play and use software thatis normally just for MS. but what do you expect when they are partners with MS.
 The only other system that is very easy is Linspire but unfortunatelly you have to join their site to get the thousands of software that you can get out of their warehouse. some free and some you buy. Even software to run games and programs made for MS.:popcorn:
 WE need to convince Ubuntu to step it up and add some of this software to their OS.
 Ubuntu has a nice look and feel but is behind many Linux systems

---

