---
title: "Unreal Tournament 2004 in Ubuntu 12.04 64-bit"
date: 2012-10-10
forum: Gaming &amp; Leisure
---

### Post by LukeLinux on 2012-10-10
I am about to tear my hair out right now after spending over an hour unsuccessfully getting UT2004 to install in Ubuntu 12.04. I've had issues with previous versions of Ubuntu and so I thought this time would be a piece of cake--I knew to download the Loki installer, use the 'export SETUP_CDROM' command to point the installer to the right place, have libstdc++ installed, and I anticipate running the game with the 'aoss' command to get sound working.

...all that knowledge apparently doesn't matter right now :mad:

So I'm doing this on a computer without a disk drive, which is part of the problem I'm sure. If I use the linux_installer.sh that came on the disk, everything works great until I get to the actual installation. It just can't find the CD. I've got an image that I made of the disk and I've tried mounting it in every imaginable place and still the installer can't find it. The Loki installer from Linux Gamers doesn't even get that far; after entering the CD key, it just freezes, although I'm assuming it suffers from the same issue of being unable to locate the disk.

What gives? With the way Ubuntu handles mounting disks one would think it would be easy to fool an installer into believing a mounted ISO is a real disk, but apparently not.

I know it's not Ubuntu's fault in and of itself, as I have the game running in the same version of Ubuntu on another computer, but it's not my main PC and I'd like to have it here, too.

Any suggestions? I've got to conquer this thing now just so that I won't have wasted an evening being defeated :p

---

### Post by borgware on 2012-10-15
It's possible to make it run under ubuntu 12.04 however, loki installer isn't going to work.  

You have to install UT2004 using either wine or windows if you dual boot.  Then copy all UT2004 files and folders to i.e. .../home/borgware/ut2004.  You can also use  /usr/local/games path if you really must.  

Download ut2004 megapack from icculus
                                  [http://treefort.icculus.org/ut2004/ut2004megapack-linux.tar.bz2](http://treefort.icculus.org/ut2004/ut2004megapack-linux.tar.bz2)
unpack (right click/extract here) then move all folders to /home/ut2004 merging/overwriting all files and folders.
Also, get the latest linux patch from icculus.
                                   
[http://treefort.icculus.org/ut2004/ut2004-lnxpatch3369-2.tar.bz2](http://treefort.icculus.org/ut2004/ut2004-lnxpatch3369-2.tar.bz2) 
  Do the same thing as with ut megapack.  

You're going to need these 2 libraries as well
                                  [http://www.unix-ag.uni-kl.de/~deusser/UT2004/ut2004-libs-x86.tar.gz]("http://www.unix-ag.uni-kl.de/%7Edeusser/UT2004")
  and for 64 bit linux
                                  [http://www.unix-ag.uni-kl.de/~deusser/UT2004/ut2004-libs-amd64.tar.gz]("http://www.unix-ag.uni-kl.de/%7Edeusser/UT2004/ut2004-libs-amd64.tar.gz")
unpack and move to ut2004 folder.

The last step is to get sound working. 
sudo apt-get install libopenal1
 Delete local openal.so file from .../ut2004/System folder then link new file like this

"example home folder path"
                                  ln -s /usr/lib/x86_64-linux-gnu/libopenal.so.1 /home/borgware/ut2004/System/openal.so

Keep in mind that the game runs so much faster and smoother under unity 2D than under unity 3D.   Hopefully ubuntu and other developers are going to solve that problem soon.
If you have problems setting the game resolution at 1920x1080 then go to /home/.ut2004/System/UT2004.ini file (hiden local folder) and change resolution from there like this
FullscreenViewportX=1920
FullscreenViewportY=1080

That's it.  Also, if you need ut2004 desktop icon you can get it from here
                           
[http://www.unix-ag.uni-kl.de/~deusser/UT2004/ut2004.xpm]("http://www.unix-ag.uni-kl.de/%7Edeusser/UT2004/ut2004.xpm")
    
I know I know not your typical game installation but be patient until we get steam under linux working.   ;-)

---

### Post by Brebs on 2012-10-15
> **LukeLinux said:**
> It just can't find the CD.
strace is a useful command, to see what an app is doing. E.g.:
```
strace -e trace=file yourinstallerprogram
```

---

### Post by auxilium on 2013-02-14
hello guys,

If this thread is still going, I am not sure if this helps a lot. But I want to share this

[https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)



Goodluck

---

### Post by Kiori on 2013-02-15
Its a real shame this isn't on steam.

---

### Post by jaime3 on 2013-12-16
> **Kiori said:**
> Its a real shame this isn't on steam.


I have Unreal Tournament 2004 in steam in Windows but odd there isn't for Linux under Linux version of Steam. :mad:

---

