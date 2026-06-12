---
title: "Ubuntu freezes"
date: 2005-05-14
forum: Desktop Environments
---

### Post by Juri on 2005-05-14
I have been trying to install Ubuntu for about 2 weeks now. Ubuntu seems to want to freeze in one of two places. If I tell atp to install pacages from internet sources then ubuntu will freeze at just after 'get:5 us.archive.ubuntu.com hoary-updates/main packages [2837B].' As my parents' use to tell me, "if it hurts to do that, then don't do that." I stopped telling apt to install from internet sources, then I get all the way to a login screen. But it seems like anytime I touch a key or the mouse I have 5 to 30 secounds before Ubuntu completly freezes.

I have though found a way to get into Ubuntu, boot into the recovery mode add '/usr/X11R6/bin' to PATH and type 'gdm.' then I get the message 'failed to initalize hal' but Ubuntu doesn't freeze. (hal is the host name of my computer) 

Thanks for your help

I am using the AMD64 5.04 install cd burned form the iso from the United States official site. I have an AMD Athlon 64 processor 3200+, and a Gigabyte K8N Pro Mobo.

if you need more info, please tell me.
Thanks again

(oh and if anyone is wondering how I solved my hard drive Problem: [http://ubuntuforums.org/showthread.php?t=31048]("http://ubuntuforums.org/showthread.php?t=31048"). I bought a new hard drive)

---

### Post by defkewl on 2005-05-14
Perhaps you have a slow internet connection. Try changing your repo to a closer mirror. Or use debian repo. CMIIW

---

### Post by ajt3nc on 2005-05-15
Just a thought ,  one of my desktops did the freeze trick and it was a bad install cd,( nero did not like ubuntu, alky 120 solved that)
My kids box was freezing up at random times and I eventually traced it to the 
ATI video card driver. 
I changed it using dpkg-reconfigure xserver-xorg command and specified the 
fglrx driver and everybody is happy.

---

### Post by NaplesBill on 2005-05-15
If you have an nVidia graphics card then it's probably freezing because of that.  If this is the case, do a search for "nvidia" and "freezes" and you should find the solution.  I can't remember what you need to do off the top of my head.

---

### Post by Juri on 2005-05-23
I have found and installed the Nvidia drivers, but this seems to have changed nouthing (except I now see a big Nvidia logo before my login screen).  any advice on how I could go about tracing the problem myself.  Or on how to get helpful information so that I can give more informed posts.  Thanks

---

