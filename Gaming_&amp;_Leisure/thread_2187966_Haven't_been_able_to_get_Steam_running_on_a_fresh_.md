---
title: "Haven't been able to get Steam running on a fresh install of 13.10"
date: 2013-11-14
forum: Gaming &amp; Leisure
---

### Post by oapeter on 2013-11-14
Hey all!

When I try to install Steam on my new install of 13.10, I get some errors. I'm hoping someone here has run into the same problem and can point me in the right direction to get it fixed. Seems like a fairly simple problem (like maybe changing file permissions mid-install), but I'm not sure.
Steam seems to install either from the .deb file or the software centre just fine (tried a few different ways), but when I try to run it the first time from the desktop, I get an error stating: 

"Couldn't set up Steam data - please contact technical support"

and when I run it from the terminal:
```

oapeter@oapeter:~$ Repairing installation, linking /home/oapeter/.steam/steam to /home/oapeter/.local/share/Steam
rm: cannot remove ‘/home/oapeter/.steam/steam’: Is a directory
Setting up Steam content in /home/oapeter/.local/share/Steam
rm: cannot remove ‘/home/oapeter/.steam/steam’: Is a directory

```

Has this happened to anyone else? 
Thanks a lot!

---

### Post by snafu006 on 2013-11-14
How did you install steam ? From the software center or did you install from terminal.

---

### Post by nat00 on 2013-11-15
You should try removing the /home/oapeter/.steam/steam file. You don't actualy have to do it from a terminal, you can just check "enable hidden files" in the file menu and go to the .steam directory.

---

### Post by oapeter on 2013-11-15
Hey guys. I tried installing it a few ways. First I downloaded the .deb file from steampowered.com and ran it through Ubuntu software center. I also tried searching the software center and installing Steam from there. Lastly I installed it from the terminal. 

I tried deleting the file as nat00 suggested, which stopped the first error, but now there appear to be more errors. 

```

Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
/home/oapeter/.local/share/Steam/steam.sh: line 755:  5754 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat &#8216;/home/oapeter/.steam/registry.vdf&#8217;: No such file or directory
Installing bootstrap /home/oapeter/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/oapeter/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
/home/oapeter/.local/share/Steam/steam.sh: line 755:  5871 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"

```

Maybe I just need to wait for a new version?

---

### Post by sffvba[e0rt on 2013-11-16
I know this is not ideal but if no-one here can assist you can always try to get assistance from here - [https://support.steampowered.com/newticket.php](https://support.steampowered.com/newticket.php) (and if you do, keep us in the loop here on how it is going so that perhaps somebody else facing the same issue can get the answer easier).

---

### Post by DanglingPointer on 2013-11-17
Were you able to solve your problem?

Since your 13.10 is fresh, have you considered just returning to the official version that Steam supports?  I'm running 12.04 LTS and everything works great.

---

### Post by oapeter on 2013-11-17
Hi!

No, I haven't got it working yet. I'm going to head over to the steampowered.com forums this morning and ask. I have steam running on 13.10 on my laptop, but I upgraded Ubuntu from a previous version. The fresh install is on my desktop, which I'm going to be completely reformatting once my current college term is finished, so I think by then the installer should support 13.10, but I'll make a decision at that time as to what version of Ubuntu to reinstall. This installation was just to test out how Ubuntu was going to do on it, and so far so good aside from this and one other thing.

Thanks!

---

### Post by sffvba[e0rt on 2013-11-17
The Steam installer works on ()buntu 13.10 just fine (well most of the time as we don't know why the OP's doesn't want to work).

---

### Post by oapeter on 2013-11-17
Would it matter that I had to install the nvidia proprietary driver to get Ubuntu stable?

---

### Post by murray-472 on 2013-12-16
So I know this is a few weeks old but it doesn't seem like any solution was found. I stumbled upon this thread trying to fix the same problem myself. What caused it for me was having some leftover files (maybe from my installation of steam in WINE) in the home folder. I went through the home folder and removed any files or folders with "steam" in their name. After re-installing, steam worked perfectly.

---

### Post by jaime3 on 2013-12-17
> **murray-472 said:**
> So I know this is a few weeks old but it doesn't seem like any solution was found. I stumbled upon this thread trying to fix the same problem myself. What caused it for me was having some leftover files (maybe from my installation of steam in WINE) in the home folder. I went through the home folder and removed any files or folders with "steam" in their name. After re-installing, steam worked perfectly.


Well..... Have you tried another version of Ubuntu. Beside 13.10 support only for few months the 12.04.3 support until 2017. Well I have no issue with Steam on 12.04.3.

---

### Post by Pawel_Pieczul on 2014-02-27
I've just had same symptoms on an updated Ubuntu 13.10.
You can actually run steam with debugger: DEBUGGER=gdb steam
When in gdb you have to enter "r" to run the app wait for the crash and see backtrace (bt).
Mine was is in 32-bit version of nVidia's OpenGL library: /usr/lib32/libGL.so.1
When I looked at this file it was a link to libGL.so.331.20, probably meaning version 331.20 of nVidia driver.
So I look at what I have installed and found another version of the drivers in /usr/lib32/nvidia-304 (304.88)
I don't know how they got there, but I can see there is a package installed nvidia-304, so if you don't have them try installing this package.

Then, you can run steam forcing to use the old libraries:
LD_LIBRARY_PATH=/usr/lib32/nvidia-304 steam

In my case steam started fine.

Cheers
Pawel

---

### Post by sigurd14-q on 2014-03-15
> **murray-472 said:**
> So I know this is a few weeks old but it doesn't seem like any solution was found. I stumbled upon this thread trying to fix the same problem myself. What caused it for me was having some leftover files (maybe from my installation of steam in WINE) in the home folder. I went through the home folder and removed any files or folders with "steam" in their name. After re-installing, steam worked perfectly.

This worked for me :)

---

### Post by saiki4116 on 2014-04-03
Hi,

I had faced the same problem, as some one mentioned in this thread, raised a ticket in steam support ticket. They have give [this]("https://support.steampowered.com/kb_article.php?ref=3134-TIAL-4638") as solution and it worked.

---

