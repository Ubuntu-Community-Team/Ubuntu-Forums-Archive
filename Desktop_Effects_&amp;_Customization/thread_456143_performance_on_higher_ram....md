---
title: "performance on higher ram..."
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by gopoo on 2007-05-27
I got a system with 512 ram , 128 mb graphics card , core duo ,...

recently i updated to 2 gb ram , but to my surprise

there aint any noticable performance gain... :O ,

as my system also got xp and vista...

xp also doesnt get any performance gain ,

only vista is faster by far ...


is there something i can do about it in ubuntu ? so that it use all my ram for improve performance.

btw , this is my laptop. :D

---

### Post by PhatStreet on 2007-05-27
You might not notice a difference because Linux's RAM management is very efficient. You'll probably notice a slight difference when you're running a ton of apps at once, but in general use, I wouldn't expect much.

On the other hand, Vista's a bit of a RAM hog. Its precaching is nice, but it's not suitable for systems with under 1 GB, hence the large performance upgrade.

---

### Post by earobinson on 2007-05-27
With Ubuntu you will only notice a difference when using a lot of ram intensive programs.

However you could look into using prefetching im just not sure of the state of prefetching and ubuntu.

Note: prefetching is when the os will load your most cominly used apps into memory with any extra memory you have.

Eg firefox will be loaded and ready to run before you run it.

---

### Post by gopoo on 2007-05-27
Is there something i can do for it ?

i have heard of preload or something...but didnt try it myself...



[SIZE="1"]I mean i got feeling of wasting 100$ for a 2 gig ram...[/SIZE]

---

### Post by earobinson on 2007-05-27
Ya I have heard of it but really dont know enough to comment on it, all I know is programs will load faster and they do it in vista

---

### Post by Ateo on 2007-05-27
You didn't get ripped off. Once you understand how Linux utilizes memory, you'll feel better.

---

### Post by gopoo on 2007-05-30
hey i got the idea.....can i use ram as a swap memory ??

---

### Post by kpolice on 2007-05-30
Do you actually use your swap partition with 2GB? I have 1.25GB of RAM and my swap is always 100% free.

---

### Post by shae on 2007-05-30
I do not reboot very often and because I have 2 GB of ram, most of my programs are cached.    I love having two gigs of ram (before I only had one)  But again I am a heavy multitasker.

---

### Post by BobCFC on 2007-06-11
You will notice it if you have 150 tabs open in Firefox like I do sometimes.  :D

I bought 8gb pc2-6400 so that my new PC will last a good few years.  I am very interested if someone can advise on taking full advantage in Ubuntu with caches and prefetching.  Sometimes Vista64 caches 7.5gig for me when installing games etc.   Pity I have no other use for Vista.  ;)


Another reason for large ram is Virtualisation ...  eg Xen or VMware Server so you can run multiple OS at same time

Oh i don't even have a swap partition lol

---

### Post by 444 on 2007-06-11
There isn't much to improve. The only possible-but-not-done thing I can think of is startup time, don't know if there's a working program for that though.

---

### Post by BobCFC on 2007-06-11
I've found a couple of useful things.

**sudo apt-get install preload**

This helps to load common libraries and applications.   Seems to work unattended I need to look into config.


**sudo apt-get install alltray**

Alltray lets you launch an application minimised to the system tray by prefixing a command with alltray.  I added a startup program in Preferences->Sessions to :

**alltray firefox**

This preloads the browser on boot.  While it takes a few seconds longer to start gnome, when I actually want firefox it starts instantly!


You can optimise linux with a bias against swap files without disabling them

sudo nano **/etc/sysctl.conf**

Add the line
**vm.swappiness=0**

This number ranges from 0-100 with 60 the default.  100 means use swap alot 0 hardly ever.


In a similar vein if you have a dual or quad core processor you can parallelise(?) the boot process 

sudo nano **/etc/init.d/rc**

change  CONCURRENCY=none  to   **CONCURRENCY=shell**


Finally use **leafpad** instead of gedit or other bloatware for insta-start like notepad.


I think the next step for me is to build my own kernel.  I have read about options such as optimise for large memory etc.
[Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel")
[Kernel Useful/Performance Tips]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507")

---

