---
title: "Unreal Tournament 2004 lag"
date: 2005-06-27
forum: Gaming &amp; Leisure
---

### Post by DarkManX4lf on 2005-06-27
as a new  user to linux i managed to get UT2004 DEMO to work nicely, only thing is i get lag....not net lag, but video lag, but it only happens on certain maps (i forget which).....but what would happen is it would be all find for a second and then when i get to a slightly crowded area it lags...but then it smooths out....its like its loading something...lags and then becomes fine...


anyone know how to fix this?


also a friend of mine let me borrow his retail UT2004 dvd, and i tried to install it but it wont let me install...in the terminal i type

cd /media/cdrom0

and then:

sh ./linux-installer.sh

but it says this after the above

./linux-installer.sh: ./linux-installer.sh: cannot execute binary file

anyone know how to fix this as well ?

---

### Post by apollo2011 on 2005-06-27
I have the UT2004 CD Set, and have been able to install it fine on both SuSE and Linux and then actually, never installed it on Ubuntu, just forwarded everything to the SuSE installation.  It runs fine on both.  First of all,my first guess would be that maybe your hardware is not good enough for the game, maybe you should try lowering the video quality settings and see if that fixes/lessens the problem.

Second, in order to install off the CDs/DVD you need to copy the linux-installer.sh off the DVD.  So browse to the DVD, copy the file temporarily to your home directory, and then go into the console and type ./linux-installer.sh (like you did but only from your home dir).  That should load the installation program and start the installation after aksing where to install.

Hope this helps you with your problems :)

---

### Post by DarkManX4lf on 2005-06-27
[QUOTE=apollo2011]I have the UT2004 CD Set, and have been able to install it fine on both SuSE and Linux and then actually, never installed it on Ubuntu, just forwarded everything to the SuSE installation.  It runs fine on both.  First of all,my first guess would be that maybe your hardware is not good enough for the game, maybe you should try lowering the video quality settings and see if that fixes/lessens the problem.

Second, in order to install off the CDs/DVD you need to copy the linux-installer.sh off the DVD.  So browse to the DVD, copy the file temporarily to your home directory, and then go into the console and type ./linux-installer.sh (like you did but only from your home dir).  That should load the installation program and start the installation after aksing where to install.

Hope this helps you with your problems :)[/QUOTE]


so my system:

ASUS A8V Deluxe 
AMD 64 3500
1 GIG Kingston DDR
Ati Radeon 9800 (oc'ed to xt)
SB Audigy 2

is not good enough ?

also i did copy the file to my home folder and then tried to run the install from there...but it still says the same thing

./linux-installer.sh: ./linux-installer.sh: cannot execute binary file

---

### Post by apollo2011 on 2005-06-27
](*,) No, that system should be plenty good enough (better than mine for sure)! :) 

I believe the problem is that the file is not executable.  In the console first type "chmod a+x linux-installer.sh" and then do "./linux-installer.sh"  There are different procedures for getting .runs, .bins, and .shs to run and quite honestly, I don't remember what you have to do for each one... :-?

---

### Post by DarkManX4lf on 2005-06-27
[QUOTE=apollo2011]](*,) No, that system should be plenty good enough (better than mine for sure)! :) 

I believe the problem is that the file is not executable.  In the console first type "chmod a+x linux-installer.sh" and then do "./linux-installer.sh"  There are different procedures for getting .runs, .bins, and .shs to run and quite honestly, I don't remember what you have to do for each one... :-?[/QUOTE]


i tried that and it still says the same thing 
bash: ./linux-installer.sh: cannot execute binary file

---

### Post by apollo2011 on 2005-06-27
OK, I believe I gave you the wrong procedure, like I said, I get them confused!

type "sh linux-installer.sh".  If it doesn't work,

then try "chmod +x linux-installer.sh"
then "./linux-installer.sh"

Hope one of these works!  :-?

---

### Post by DarkManX4lf on 2005-06-27
thanks, but that stiill did not work, i dont get it...i dont see why it wont install in linux using the linux installer....the real funny thing is i got it to install in cedega, although when trying to run the game there were some errors....


there must be a way !!!!

---

### Post by apollo2011 on 2005-06-27
that's strange cuz I looked it up...

---

### Post by DarkManX4lf on 2005-06-27
yea i dont know why it wont open either.

---

### Post by apollo2011 on 2005-06-27
You did copy the whole file not just linked to it or something strange like that right?

---

### Post by DarkManX4lf on 2005-06-27
yea i copied the whole file its 28.3MB

---

### Post by DarkManX4lf on 2005-06-28
well i found out a little more about the lag i have, i see that its only on the onsalught maps, the ctf maps are pretty much ok....

---

### Post by noerej on 2005-06-28
I have lag on the Onslaught maps and I'm not the only one either. Lowering the video quality sometimes helps, but your best bet is to find a better server.

---

### Post by Zeroedout on 2005-06-28
outta curiousity, did you copy the file to your home directry? If so, when you right click it, and hit the permissions, who is allowed to execute?

---

### Post by apollo2011 on 2005-06-28
[QUOTE=noerej]I have lag on the Onslaught maps and I'm not the only one either. Lowering the video quality sometimes helps, but your best bet is to find a better server.[/QUOTE]

I think the lag he was having was hardware-based.  He said it wasn't net lag.I would assume the kind of lag he has occurs even you are playing Instant Action with just bots on your local computer.

---

### Post by DarkManX4lf on 2005-06-29
i made sure everyone has permissions to it.  well there is one thing that could be a problem ?  the dvd that i have is the german version...or at least thats what it says on the dvd label in ubuntu...i bought a copy and i am awaiting its arrival so hopefully that  one will work

---

### Post by smack on 2005-06-29
You don't need to copy the installer to your home directory.

Don't navigate to the cd and then launch the installer because when it asks you to swap CDs it won't let you unmount/eject because bash(or whatever shell you use) will be using your CDROM.

Instead keep your shell out of the CD and just use a fully qualified path to the installer. Example 'sh /media/cdrom/installer.sh'(right) vs './installer.sh'(wrong).

---

### Post by DarkManX4lf on 2005-06-29
[QUOTE=smack]You don't need to copy the installer to your home directory.

Don't navigate to the cd and then launch the installer because when it asks you to swap CDs it won't let you unmount/eject because bash(or whatever shell you use) will be using your CDROM.

Instead keep your shell out of the CD and just use a fully qualified path to the installer. Example 'sh /media/cdrom/installer.sh'(right) vs './installer.sh'(wrong).[/QUOTE]
 thanks but that did not work here is what i did and what it said:

root@ubuntu:~ # sh /media/cdrom/linux-installer.sh
/media/cdrom/linux-installer.sh: /media/cdrom/linux-installer.sh: cannot execute binary file

i am always logged in as root btw.

---

### Post by apollo2011 on 2005-06-29
that is really bizarre.

---

### Post by DarkManX4lf on 2005-06-30
yea it is, im going to wait for my retail version to arrive and see if i can install with that.

---

### Post by DarkManX4lf on 2005-07-05
yea so i got my retail version, and the install works now.

---

### Post by apollo2011 on 2005-07-06
Is there still lag when you play some of the maps?

---

### Post by DarkManX4lf on 2005-07-06
yea there is, its only the onslaught maps tho, all the other gametypes/maps are perfecly fine and just as good as in windows, but the onslaught is laggy,

---

### Post by DarkManX4lf on 2005-07-06
i think i got rid of the lag, i installed the new drivers from the ati website, and i think there is no more lag on  onslaught maps gotta play more onilne to check.

---

### Post by Djeepy46234 on 2005-07-07
It's slower on Linux than on Windows for some games. I'm lagging so much only with those OpenGL screensavers...

---

### Post by apollo2011 on 2005-07-07
[QUOTE=DarkManX4lf]i think i got rid of the lag, i installed the new drivers from the ati website, and i think there is no more lag on  onslaught maps gotta play more onilne to check.[/QUOTE]
 Sounds like you got it working pretty good now.

---

### Post by DarkManX4lf on 2005-07-07
[QUOTE=apollo2011]Sounds like you got it working pretty good now.[/QUOTE]

yea once i got the ATI drivers from the ATI site working onslaught runs smoother.

---

### Post by MrPsycho on 2005-07-08
[QUOTE=DarkManX4lf]i think i got rid of the lag, i installed the new drivers from the ati website, and i think there is no more lag on  onslaught maps gotta play more onilne to check.[/QUOTE]
 I have this exact same problem.

Retail version
Athlon 1700+
G4 ti 4600
1gb ram
audigy

When I scale down the vid quality, the pausing is less frequent.  Its very strange because it feels like its loading something.  With the graphics all the way up the pausing is as frequent as every 30 seconds.

For a time, i thought the problem was related to the audigy, but removing the card still produced the same results.  Right now I'm going to test my theory that its related to the fact that ubuntu puts the swap partition on the end of the drive.  I've moved my swap to the beginning and I'm going to see if it makes a difference.

---

### Post by DarkManX4lf on 2005-07-08
yea my lag is gone completely, the new ATI drivers did it, although in linux i get lower fps than i do in windows.

---

### Post by MrPsycho on 2005-07-08
Moving my swap to the front of the drive didnt fix it :( .  Any suggestions?

---

### Post by evilghost on 2005-07-18
[QUOTE=MrPsycho]Moving my swap to the front of the drive didnt fix it :( .  Any suggestions?[/QUOTE]

You're right.  You need to adjust the amount of preload cache.  In your ~/.ut2004/System/UT2004.ini set the line:

CacheSizeMegs=512

This line occurs in two places.  This is assuming you have at least 1GB of RAM.  If you have less, adjust that value accordingly.

Additionally, set:
VARSize=64 from 32 if you have a video card with at least 128MB of RAM.

---

