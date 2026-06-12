---
title: "Unreal Tournament 2004 install"
date: 2007-10-05
forum: Gaming &amp; Leisure
---

### Post by Absolut139 on 2007-10-05
I realize this is quite an old topic but I really need some help as I am completely new to Linux and cannot seem to get this thing working.

Bought UT 2004 DVD editors choice edition and for some reason it does not seem to have the linux-installer.sh file.  I attempted to download this file from a link i found on one of these forums.  I chmod a+x the file as instructed somewhere, then ran:
rick@rick-desktop:~/Desktop$ ./linux-installer.sh
Copying to a temporary location...
Verifying archive integrity...Error in MD5 checksums: f9a3c76dee8651520db812e5e285d178 is different from 34d72f0a4c06f7da084a8a1653a0bae4
I'm assuming that not passing the MD5 checksums is a result of the file being corrupt?  I cannot seem to find any other linux-installer.sh link thats active.  Am i correct in assuming that the checksums error is a result of a corrupt download? If so does anyone know a good link of this file.  Or, would it be possible to just download the UT2004 linux demo, and then enter the cd key in to unlock the demo version? I need to get this thing working, someone please help a linux newb that just doesn't want to go back to M$.
I'm running Feisty Fawn on Athlon 64 x2 5400+, on Asus m2n32 sli deluxe, 2gb ddr2 ram, bfg geforce 7950 OC, and WD Raptor-X 150 gig.
New system, fresh install of ubuntu i386 - really want this to work out.
Thanks guys.:confused:

---

### Post by nalmeth on 2007-10-05
That sux, I had the 5 CD installer which has the install file.
One cool thing is that you don't need the CD to play on linux, at least through the CD install method.

Anyway,

I think you can find the file you need on this page, or if not, somewhere on this site:
[http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17)

---

### Post by koer on 2007-10-05
> **Absolut139 said:**
> I realize this is quite an old topic but I really need some help as I am completely new to Linux and cannot seem to get this thing working.

Bought UT 2004 DVD editors choice edition and for some reason it does not seem to have the linux-installer.sh file.  I attempted to download this file from a link i found on one of these forums.  I chmod a+x the file as instructed somewhere, then ran:
rick@rick-desktop:~/Desktop$ ./linux-installer.sh
Copying to a temporary location...
Verifying archive integrity...Error in MD5 checksums: f9a3c76dee8651520db812e5e285d178 is different from 34d72f0a4c06f7da084a8a1653a0bae4
I'm assuming that not passing the MD5 checksums is a result of the file being corrupt?  I cannot seem to find any other linux-installer.sh link thats active.  Am i correct in assuming that the checksums error is a result of a corrupt download? If so does anyone know a good link of this file.  Or, would it be possible to just download the UT2004 linux demo, and then enter the cd key in to unlock the demo version? I need to get this thing working, someone please help a linux newb that just doesn't want to go back to M$.
I'm running Feisty Fawn on Athlon 64 x2 5400+, on Asus m2n32 sli deluxe, 2gb ddr2 ram, bfg geforce 7950 OC, and WD Raptor-X 150 gig.
New system, fresh install of ubuntu i386 - really want this to work out.
Thanks guys.:confused:

hey , i had that problem too..... you know how i fixed it ? well so happens that i was using the wrong cd ( i have ur same editors choice version so this is likely to work) there is a cd that says "cd installer disk 1"
well that is the wrong one , search the 7 disks , one should say only "install disk" and that one contains the linux installer , hope that helps , oh and i havnt been able to install it cause i dont have enough space on my partition , im dying to try it out :( 

well if it works , enjoy it for me :popcorn:

---

### Post by fadastic on 2007-10-05
koer, he says he has the DVD version, which I assume is on one disc. I, too, have the DVD version of UT2004 and would like to know how to install it.

---

### Post by Absolut139 on 2007-10-05
Yeh, the DVD only has Disk 1-5 folders , Autorun Data folder, manual.pdf (which says nothing about linux) and the .exe ... I downloaded and extracted the patch but that has no installer or anything with it.  I'm back to square one, but thanks for the help, I really just need to get my hands on linux-installer.sh

---

### Post by DoktorSeven on 2007-10-05
Don't know if that's the same as the Midway Anthology (probably not) but there's a thread [here](http://ubuntuforums.org/showthread.php?t=394706&highlight=ut+2004+install) on how to install it; even if it's not the same, maybe the procedure is similar enough.

I'm sure if I had that DVD I could figure out how to get it going (probably just a matter of uncompressing and renaming from the Microsoft install files as done on the link), but I don't own UT2k4, unfortunately.

---

### Post by fadastic on 2007-10-06
> **Absolut139 said:**
> Yeh, the DVD only has Disk 1-5 folders , Autorun Data folder, manual.pdf (which says nothing about linux) and the .exe ... I downloaded and extracted the patch but that has no installer or anything with it.  I'm back to square one, but thanks for the help, I really just need to get my hands on linux-installer.sh

Hey, dude, I found it here: [http://lackteam.free.fr/download/linux-installer.sh](http://lackteam.free.fr/download/linux-installer.sh)

But, when I run it, I get:

```
Copying to a temporary location...
Verifying archive integrity...Error in MD5 checksums: f9a3c76dee8651520db812e5e285d178 is different from 34d72f0a4c06f7da084a8a1653a0bae4

```

I'm guessing it's not working because it's not in the same directory as the CD?

---

### Post by Absolut139 on 2007-10-06
> **fadastic said:**
> Hey, dude, I found it here: [http://lackteam.free.fr/download/linux-installer.sh](http://lackteam.free.fr/download/linux-installer.sh)

But, when I run it, I get:

```
Copying to a temporary location...
Verifying archive integrity...Error in MD5 checksums: f9a3c76dee8651520db812e5e285d178 is different from 34d72f0a4c06f7da084a8a1653a0bae4

```

I'm guessing it's not working because it's not in the same directory as the CD?

I don't think so, I downloaded the file from that same link, I am under the impression that checksums error has something to do with file integrity "the MD5 hash is commonly used to verify the integrity of files "-Wiki , so I think thats a bad link..
I'm going to keep trying

---

### Post by Absolut139 on 2007-10-06
Ok people, problem solved...
Go [here]("http://www.liflg.org/forum/viewtopic.php?t=848&postdays=0&postorder=asc&start=30")
to get the scoop on what happened.
Or [just download this file]("http://liflg.org/files/testinstaller5.run")
This will fix the installation for the Midway Editor's Choice edition
Yay, thanks to kratz00

---

### Post by Absolut139 on 2007-10-06
I'm starting to lose patience...
UT installed fine and is capable of running, but...the game is laggy as hell.  glxgears gets over 10,000 fps, but UT only gets an avg of like 20. Something is terribly wrong.  Anyone know what the problem is? I have installed envy nvidia drivers for my Nvidia geforce 7950 GT. Dont understand it.

***Solved - with a fresh install.

---

### Post by pyro2927 on 2009-10-07
I know it's been a long time since this has been posted to, but has anyone found a solution?

---

### Post by Absolut139 on 2009-10-07
If you looked at the earlier post I put up a link to a website with installers that you can use with your UT disc.  The installer can be found here : [http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17)

---

