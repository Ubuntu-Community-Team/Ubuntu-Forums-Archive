---
title: "HOWTO: Unreal Tournament too fast"
date: 2006-12-17
forum: Gaming &amp; Leisure
---

### Post by steve.horsley on 2006-12-17
I have seen a number of threads from people where Unreal Tournament (the original GOTY version) runs too fast. Well, my old game turned up behind the sofa last week, so I installed it on my new PC and had the same problem. I found a few suggested solutions, one of which almost worked sometimes. 

It seems the problem is with CPUs whos clock rate changes when they get busy, confusing the game timings. One suggested fix ran a second process for a few seconds as the game started, so that the timing loop was calibrated while the CPU was busy. I found that this works sometimes, but not always. I think firstly, sometimes the game finished calibrating before the CPU changed gear. And I also found that joining a network game sometimes caused the came to recalibrate.

I have a solution that works for me, and that is to launch a second process that wastes CPU doing nothing for hte entire duration of the game. This process is launched a few seconds before the game starts to ensure that the CPU has changed speed when the game calibrates, and is run at a low task priority so it doesn't interfere with game play. For me, anyway, the game play is smooth and consistent and always at the right speed.

Firstly,  if the installer created a symlink to ut somewhere, you may need to delete that again. You can find out which ut gets executed when you issue the command ut by using the command **which ut**. You want it to delete this symlink.

Second, I installed ut in the directory /opt/ut. To launch the game without the other stuff, just launch /opt/ut/ut. You may have chosen somewhere different and will need to adjust the script ut below accordingly.

Third,  I created a small script that uses up all available CPU. I don't do shell scripting, so this is  a python script. I created a file /usr/local/bin/utmakebusy with the following contents:
```
#!/usr/bin/python
x = 0
while 1:
    x += 1

```
Make this executable with the command **sudo chmod +x /usr/local/bin/utmakebusy**

Fourth, a script that runs utmakebusy in the background at low priority and then runs the game. The file name is /usr/local/bin/ut, with the following contents:
```
nice -n 19 /usr/local/bin/utmakebusy &
sleep 3
/opt/ut/ut
killall utmakebusy

```
This script also needs making executable. Now you can start Unreal Tournament with the command ut and all shoud be well.

---

### Post by aidanr on 2006-12-17
nice, must try this out:KS

---

### Post by nfg2u on 2006-12-20
Thank you Thank you Thank you and Cheers Mate is all I can say! 
This worked for me! 
:)

---

### Post by Dritzen on 2007-01-27
This worked like a charm.  Thank you!

---

### Post by Dritzen on 2007-01-27
By the way, you can use utmakebusy with Unreal Gold as well.

I used this script and it works fine for me:

nice -n 19 /usr/local/bin/utmakebusy &
sleep 3
cd /home/username/games/unrealgold
./unrealgold
killall utmakebusy

---

### Post by cookfromfrozen on 2007-02-11
Another thing you could try is to turn off whatever causes the CPU speed to step up/down in the BIOS.  

On Intel laptops, this is called SpeedStep and can sometimes be turned off in the BIOS.

On AMD64 chips it is called Cool'n'Quiet.

In some BIOSes it is called different things, such as CPU speed stepping.

---

### Post by szantaii on 2007-03-20
Maybe this could help someone too:

[http://www.ubuntuforums.org/showthread.php?p=2326019#post2326019](http://www.ubuntuforums.org/showthread.php?p=2326019#post2326019)

---

### Post by BLTicklemonster on 2008-06-13
[http://www.fingel.com/ut/howtos/utonlinux.html](http://www.fingel.com/ut/howtos/utonlinux.html)

Is what I did.

---

### Post by dr.klepp on 2008-08-27
In fact you can kill the "utmakebusy" after a few seconds when the game is startet. This helps on things like eeepc to keep a cool engine :)

---

### Post by Diskdoc on 2010-11-20
Brilliant, thanks!

---

### Post by jaypmcwilliams on 2011-01-06
> **steve.horsley said:**
> I have seen a number of threads from people where Unreal Tournament (the original GOTY version) runs too fast. Well, my old game turned up behind the sofa last week, so I installed it on my new PC and had the same problem. I found a few suggested solutions, one of which almost worked sometimes. 

It seems the problem is with CPUs whos clock rate changes when they get busy, confusing the game timings. One suggested fix ran a second process for a few seconds as the game started, so that the timing loop was calibrated while the CPU was busy. I found that this works sometimes, but not always. I think firstly, sometimes the game finished calibrating before the CPU changed gear. And I also found that joining a network game sometimes caused the came to recalibrate.

I have a solution that works for me, and that is to launch a second process that wastes CPU doing nothing for hte entire duration of the game. This process is launched a few seconds before the game starts to ensure that the CPU has changed speed when the game calibrates, and is run at a low task priority so it doesn't interfere with game play. For me, anyway, the game play is smooth and consistent and always at the right speed.

Firstly,  if the installer created a symlink to ut somewhere, you may need to delete that again. You can find out which ut gets executed when you issue the command ut by using the command **which ut**. You want it to delete this symlink.

Second, I installed ut in the directory /opt/ut. To launch the game without the other stuff, just launch /opt/ut/ut. You may have chosen somewhere different and will need to adjust the script ut below accordingly.

Third,  I created a small script that uses up all available CPU. I don't do shell scripting, so this is  a python script. I created a file /usr/local/bin/utmakebusy with the following contents:
```
#!/usr/bin/python
x = 0
while 1:
    x += 1

```
Make this executable with the command **sudo chmod +x /usr/local/bin/utmakebusy**

Fourth, a script that runs utmakebusy in the background at low priority and then runs the game. The file name is /usr/local/bin/ut, with the following contents:
```
nice -n 19 /usr/local/bin/utmakebusy &
sleep 3
/opt/ut/ut
killall utmakebusy

```
This script also needs making executable. Now you can start Unreal Tournament with the command ut and all shoud be well.

YOU'RE AWESOME!!!!!!!!!!!! TOTALLY WORKED!!!! TYVM.   I made a few modifications though. I installed UT to my /home/MINE/ut dir & put the 2 files in the home dir too & adjusted the directions in the 2 files. THANK YOU AGAIN, Jay

---

### Post by Perfect Storm on 2011-01-06
Necromancing. Thread closed.

---

