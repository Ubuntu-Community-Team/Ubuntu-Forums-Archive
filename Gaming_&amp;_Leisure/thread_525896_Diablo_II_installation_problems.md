---
title: "Diablo II installation problems"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by TH3TH1NG on 2007-08-14
Hi, I have installed Ubuntu 7.04 last week and I love it, but I'd really like to install Diablo II. I have installed successfully Pharaoh, but I have problems while installing Diablo 2. When it is time to swap the Instal Disk to play disk, I use wine eject d: then put the Play Disk, but when I click on "Ok" nothing moves, like if I hadn't put the Play Disk.

Thank you for your help.

---

### Post by cjl2301 on 2007-08-15
Perhaps try the instructions here:

[http://ubuntuforums.org/showthread.php?t=443821](http://ubuntuforums.org/showthread.php?t=443821)

---

### Post by TH3TH1NG on 2007-08-15
I am using 2 cd tray, maybe it causes the problem. How do I configure wine with two cdroms?

---

### Post by TH3TH1NG on 2007-08-18
I have searched for answers but I can't figure out how to configure my cd drives. When I use the command : ls -la ~/.wine/dosdevices/

total 8
drwxr-xr-x 2 root root 4096 2007-08-18 12:51 .
drwxr-xr-x 4 root root 4096 2007-08-18 12:47 ..
lrwxrwxrwx 1 root root   14 2007-08-18 12:47 a: -> /media/floppy0
lrwxrwxrwx 1 root root   10 2007-08-10 14:20 c: -> ../drive_c
lrwxrwxrwx 1 root root   10 2007-08-18 12:51 cdrom -> /mnt/cdrom
lrwxrwxrwx 1 root root   13 2007-08-18 12:15 d: -> /media/cdrom0
lrwxrwxrwx 1 root root    8 2007-08-10 14:20 d:: -> /dev/hdb
lrwxrwxrwx 1 root root   14 2007-08-18 12:41 e: -> /media/PHARAON
lrwxrwxrwx 1 root root    8 2007-08-15 08:56 e:: -> /dev/hdd
lrwxrwxrwx 1 root root    1 2007-08-18 12:47 f: -> /
lrwxrwxrwx 1 root root   14 2007-08-18 12:47 h: -> /home/thething

How can I configure this so I can install games with wine?

---

### Post by cogadh on 2007-08-18
Run winecfg, go to the Drives tab, then hit Autodetect, it should set up both your drives correctly. Then when the game asks for the second disk, just tell it to go to the second drive (if it gives you the option to do that).

---

### Post by TH3TH1NG on 2007-08-18
I've done autodetect to set my drives but it still doesn't work. My default cd tray is E:, so where do I cd before installing? cd /media/hdd ?

---

### Post by cogadh on 2007-08-18
Don't cd to the drive at all, that will definitely prevent the tray from ejecting. Instead run Wine with the full mount path, like this:
```
wine /media/cdrom0/setup.exe
```
I believe Ubuntu uses the "/media/cdrom0" mount point by default, so just change the command to reflect the actual install executable.

---

### Post by TH3TH1NG on 2007-08-19
When I do wine /media/cdrom0/setup.exe, it answers

 wineserver: could not save registry branch to /home/thething/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/thething/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/thething/.wine/user.reg : Permission denied

Then I do it with sudo but I'm not supposed to use wine as sudo right?

---

### Post by TH3TH1NG on 2007-08-19
The installation finally worked!!! Thanks for your help! I still have a little problem, but it has nothing to do with linux. When I try to play on B.net it says "Unable to connect, if you are using a modem please contact your internet service provider". The game was working perfectly two weeks ago and I have change nothing in my modem settings, is there a way to reset the modem or any other way to correct this problem? I am using a D-link routeur also.

Thanks a lot for your help!

Oh and by the way how do I make a icon to launch Diablo instead of writing the command every times?

---

### Post by Zimbaly on 2007-08-20
I can't answer your b.net thing, but under applications there's a folder that says wine at the bottom... least for me and I go in there and there's a thing for Diablo 2. Click on that and shazam = P

So nice to play D2 eh = P

---

### Post by DARKGuy on 2007-08-20
How are you running Diablo II? I mean, what do you type in the terminal?

---

### Post by DARKGuy on 2007-08-20
Please delete me, accidental double post :lolflag:

---

### Post by TH3TH1NG on 2007-08-20
I type :
wine /thewholepath/Diablo II/D2_loader.exe

---

### Post by DARKGuy on 2007-08-20
> **TH3TH1NG said:**
> I type :
wine /thewholepath/Diablo II/D2_loader.exe

That's the problem.

Try doing:
> 
cd /thewholepath/Diablo II/
wine D2_loader.exe


---

