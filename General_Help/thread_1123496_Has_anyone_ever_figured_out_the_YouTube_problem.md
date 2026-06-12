---
title: "Has anyone ever figured out the YouTube problem?"
date: 2009-04-12
forum: General Help
---

### Post by Jimmmac1 on 2009-04-12
Hi all

My firefox still freezes when I try to run a youtube video.  I am using 8.10 and have Flash 10 installed along with the non-free plug-in and it still doesn't work.  I have googled it a number of times and looked on the forum, but don't seem to see anything that I haven't tried.  Probably have a lot of junk on my computer from the various attempts.  Thanks for your help. 

Jim

---

### Post by connorh123 on 2009-04-12
I too, would like some help with this problem.

---

### Post by khelben1979 on 2009-04-12
The flash player needs to get downloaded directly from the Adobe website, it seems. Look [here]("http://www.psychocats.net/ubuntu/flash") for more information.

Maybe it can help?

---

### Post by SuperSonic4 on 2009-04-12
It also depends on if you're running 32 bit or 64 bit firefox. You can go to help -> about in firefox to check

---

### Post by bumanie on 2009-04-12
[This]("http://www.myscienceisbetter.info/64bit/") is the only thing that got flash working on my 64bit ubuntu. It's still in alpha stage, but is stable at resent. I had no picture, no sound on you tube until following this.

---

### Post by Cloudiz on 2009-04-12
Ok, im a total noob to Ubuntu/PCs. 
Need some help adding that file, in the link the poster above me linked
In the end of that post it says 'Grab the Ubuntu script here, chmod +x and execute it.'
Now, can someone explain me how i do this? 
Do i have to type chmod +x /home/daniel/Desktop? (downloaded the file and my download location is my desktop, daniel is my username)

---

### Post by Michael.Godawski on 2009-04-12
hi does this help, taken from my terminal:

```
michael@michael-laptop:~$ cd Desktop
michael@michael-laptop:~/Desktop$ ls
00028_handbook.pdf  header.php~                      new file~     single.php~
footer.php          home.php                         robots.txt~   style.css~
footer.php~         index.php                        sidebar.php
header.php          native-64bit-flash-installer.sh  sidebar.php~
michael@michael-laptop:~/Desktop$ chmod +x native-64bit-flash-installer.sh 
michael@michael-laptop:~/Desktop$ ./native-64bit-flash-installer.sh
Stopping any Firefox that might be running
[sudo] password for michael: 
Removing any other flash plugin previously installed:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  menu sharutils bochsbios libnfnetlink0 p7zip blt vde2 libt1-5 vgabios
  lesstif2 tcl8.5 libvdemgmt0 libnetfilter-queue1 tk8.4 tk8.5 xpdf-common
  libvdeplug2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168kB disk space will be freed.
(Reading database ... 151500 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
Installing Flash Player 10
--2009-04-12 19:08:41--  http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
Resolving download.macromedia.com... 84.53.167.191
Connecting to download.macromedia.com|84.53.167.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3729613 (3.6M) [application/x-gzip]
Saving to: `libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz'

100%[======================================>] 3,729,613    240K/s   in 15s     

2009-04-12 19:08:56 (240 KB/s) - `libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz' saved [3729613/3729613]

libflashplayer.so
Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it.

```

---

### Post by nebileix on 2009-04-12
Check your firefox add-ons for 'Shockwave Flash version 10.0 r22'

If its not there

```
sudo apt-get install swfdec-mozilla libswfdec-0.8-0 adobe-flashplugin 
```

thats how it solve mind.

Gd luck.

---

### Post by connorh123 on 2009-04-12
I just installed Ubuntu 8.10, and my youtube problem is fixed :)

---

### Post by blackbird3216 on 2009-04-12
> **Jimmmac1 said:**
> Hi all

My firefox still freezes when I try to run a youtube video.  I am using 8.10 and have Flash 10 installed along with the non-free plug-in and it still doesn't work.  I have googled it a number of times and looked on the forum, but don't seem to see anything that I haven't tried.  Probably have a lot of junk on my computer from the various attempts.  Thanks for your help. 

Jim
What's the "nonfree plugin"? I use 8.10 and Youtube is fine. Just install Flash from the repositories.

---

### Post by Lunx on 2009-04-12
> **blackbird3216 said:**
> What's the "nonfree plugin"? I use 8.10 and Youtube is fine. Just install Flash from the repositories.

Nonfree is the official plugin from Adobe, so you need to agree with their terms of use. I tried using other versions, but for me they don't work in many instances, so I just accept the fact and install it. Does solve many flash related problems

---

### Post by DeMus on 2009-04-12
> **bumanie said:**
> [This]("http://www.myscienceisbetter.info/64bit/") is the only thing that got flash working on my 64bit ubuntu. It's still in alpha stage, but is stable at resent. I had no picture, no sound on you tube until following this.

[This]("http://www.myscienceisbetter.info/64bit/") really works, I just tried it. Before it I had a different  Flashplayer and sometimes it would work, sometimes I would get a grey area on Youtube. After a reload the movie sometimes would start. Now it just starts every time.
Great job. Thanks a lot.

---

### Post by Jimmmac1 on 2009-04-15
Hi all

Thanks for your responses.  I have a 32 bit computer, so the 64  bit probably won't do me much good.  I also ran this

sudo apt-get install swfdec-mozilla libswfdec-0.8-0 adobe-flashplugin

and it says I have everything there.  Still not playing the Youtube movies though.  Not sure what to do now. 

Jim

---

### Post by khelben1979 on 2009-04-15
> **Jimmmac1 said:**
> Hi all

Thanks for your responses.  I have a 32 bit computer, so the 64  bit probably won't do me much good.  I also ran this

sudo apt-get install swfdec-mozilla libswfdec-0.8-0 adobe-flashplugin

and it says I have everything there.  Still not playing the Youtube movies though.  Not sure what to do now. 

Jim

Did you download the Adobe player from the Adobe website? It does support 32bit Linux operating systems as well.

---

### Post by Jimmmac1 on 2009-04-16
Hi all

Thanks for the help.  I finally got it by running the shell script earlier in the post.  Now I can listen to Susan Boyle live.  If you haven't heard it, take a listen to this.  

[http://www.youtube.com/watch?v=9lp0IWv8QZY](http://www.youtube.com/watch?v=9lp0IWv8QZY)

Thanks all

Jim

---

### Post by psyke83 on 2009-04-23
> **Jimmmac1 said:**
> Hi all

My firefox still freezes when I try to run a youtube video.  I am using 8.10 and have Flash 10 installed along with the non-free plug-in and it still doesn't work.  I have googled it a number of times and looked on the forum, but don't seem to see anything that I haven't tried.  Probably have a lot of junk on my computer from the various attempts.  Thanks for your help. 

Jim

It's highly likely to be caused by [libflashsupport]("https://bugs.launchpad.net/bugs/192888").

The solution is to remove it. If you have audio problems, refer to the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide for more information.

---

