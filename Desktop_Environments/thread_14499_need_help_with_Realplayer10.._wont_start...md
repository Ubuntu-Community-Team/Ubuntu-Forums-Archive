---
title: "need help with Realplayer10.. wont start.."
date: 2005-02-07
forum: Desktop Environments
---

### Post by rapala61 on 2005-02-07
Im having this weird problem with RealPlayer, i installed as the howto indicates but for some reason it wont start.. missing any libs???.. or it just cuz im using hoary array 4??  and if i wanted to uninstall it , i can just erase /opt/mediaplayer right??

Tia!

---

### Post by Funraiser on 2005-03-01
I had a similar prob: try the following after having installed realplayer from ubuntuguide.org: Click applications/multimedia and right click on RealPlayer10, choose properties . In "command" field browse /home/yourname/RealPlayer/realplay.

It looks like this link in the launcher is not pointing in the right direction.
It worked for me but I have to do this everytime i want to use realplayer. Trying to find a way to make this work for good.

Good luck Ubuntian.

---

### Post by bored2k on 2005-03-01
the .bin install went perfect on me , also the panel short.cut


make sure during the installation u selected for all users to be able 2 run it

---

### Post by luvdemheels on 2005-03-01
I downloaded the RealPlayerGOLD.bin from the real website and installed it and like above, it went perfect.

---

### Post by doitashimashite on 2005-03-02
De-install the current package. Then install it again. Like this:

Download the RealPlayer package from [http://www.real.com/linux/](http://www.real.com/linux/)

Installation:

$ cd browse_to_your_download_folder
$ chmod 700 RealPlayer10GOLD.bin
$ sudo ./RealPlayer10GOLD.bin

Enter the complete path to the directory where you want RealPlayer to be installed. It is important that you specify the full pathname of the directory and that you have write privileges to that directory.

Directory:  [/home/chua/RealPlayer]: /opt/RealPlayer

You have selected the following RealPlayer configuration:
Destination:            /opt/RealPlayer
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y

enter the prefix for symbolic links [/usr]: /usr

Enter

That's it!

Have fun

---

### Post by madzzoni on 2005-03-20
[QUOTE=doitashimashite]De-install the current package. Then install it again. Like this:

Download the RealPlayer package from [http://www.real.com/linux/](http://www.real.com/linux/)

Installation:

$ cd browse_to_your_download_folder
$ chmod 700 RealPlayer10GOLD.bin
$ sudo ./RealPlayer10GOLD.bin

Enter the complete path to the directory where you want RealPlayer to be installed. It is important that you specify the full pathname of the directory and that you have write privileges to that directory.

Directory:  [/home/chua/RealPlayer]: /opt/RealPlayer

You have selected the following RealPlayer configuration:
Destination:            /opt/RealPlayer
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y

enter the prefix for symbolic links [/usr]: /usr

Enter

That's it!

Have fun[/QUOTE]

i followed this guide, but still RealPlayer wont start. Nothing happens when clicking on the launcher!

---

### Post by hantsy on 2005-03-20
Some .deb packages are avaible for Debian-Like OS (such as Linspire4.5/5,Xandros...) on the offical site.
Please refer to:
[https://player.helixcommunity.org/2004/downloads/distributionbuilds.html](https://player.helixcommunity.org/2004/downloads/distributionbuilds.html)
I use the package for linspire 5 directly, It works well .

---

### Post by NuSYS on 2005-03-30
try to do this:
go to System-preferences-audio and in the sound preferences (general tab) unceck enable soundserver.

---

### Post by Raija on 2005-03-31
[QUOTE=NuSYS]try to do this:
go to System-preferences-audio and in the sound preferences (general tab) unceck enable soundserver.[/QUOTE]

Thanks! 

It works!  :smile: Now I can see the news! 

In my earlier 5.04 installation  2-3 weeks ago it worked without these problems.

---

### Post by madzzoni on 2005-03-31
[QUOTE=NuSYS]try to do this:
go to System-preferences-audio and in the sound preferences (general tab) unceck enable soundserver.[/QUOTE]

Thanks at lot mate! Now even my RealPlayer 10 works perfectly! I'll try to install it ten times without success.

I'm a very happy man now! :-D

---

### Post by beerorkid on 2005-04-19
wow!!!!!!!

it was such an easy fix thanks NuSYS

I decided to upgrade to hoary from a heavily modified warty on my work machine.  After multiple installs not being able to use realplayer bummed me out, I tried the other posts on how to solve this problem to no avail.

I run a live real stream at work, it is important that I be able to monitor it with the real player.

real on hoary, horay!!!

One question though what does unchecking that do, and can or do I need to renable it?

---

