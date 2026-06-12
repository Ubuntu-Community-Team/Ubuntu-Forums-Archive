---
title: "Can't get NWN to run"
date: 2006-12-01
forum: Gaming &amp; Leisure
---

### Post by The Iron Curtain on 2006-12-01
Hello all, Linux Newbie here,

I posted this in the Absolute Beginners forum, but it ended up with 0 replies. I hope I'm not doing anything wrong by posting it here.

I wanted to play neverwinter nights on my newly installed Ubuntu 6.06. I followed the instructions [here]("http://nwn.bioware.com/downloads/linuxclient.html"). I downloaded the files into my /tmp folder and extracted them into /opt, following the instructions for the client resources. I then downloaded the latest patch, following instructions [here]("http://nwn.bioware.com/support/patch_linux168.html"). However... . when I did ./nwn , the game wouldn't run. (BTW, I'm doing this all from teh terminal.) Here's what I got:

```

dfoer@dfoer-laptop:/opt/nwn$ ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
dfoer@dfoer-laptop:/opt/nwn$    

```

So, what do I need to do to play NWN?

Thank you.

---

### Post by diepruis on 2006-12-01
Did you install SDL?

Please type the following and post the output:

```

sudo aptitude search sdl | grep ^i
ls /usr/lib | grep SDL

```

---

### Post by leech on 2006-12-01
Look in my SIG

Leech

---

### Post by The Iron Curtain on 2006-12-01
Here's what I got:

```

dfoer@dfoer-laptop:~$ sudo aptitude search sdl | grep ^i
Password:
i A libsdl-image1.2                 - image loading library for Simple DirectMed
i A libsdl-mixer1.2                 - mixer library for Simple DirectMedia Layer
i   libsdl1.2debian                 - Simple DirectMedia Layer
i   libsdl1.2debian-alsa            - Simple DirectMedia Layer (with X11 and ALS
dfoer@dfoer-laptop:~$ ls /usr/lib | grep SDL
libSDL-1.2.so.0
libSDL-1.2.so.0.7.2
libSDL.a
libSDL_image-1.2.so.0
libSDL_image-1.2.so.0.1.3
libSDL.la
libSDLmain.a
libSDL_mixer-1.2.so.0
libSDL_mixer-1.2.so.0.2.4
libSDL.so
dfoer@dfoer-laptop:~$


```

---

### Post by diepruis on 2006-12-02
You might be missing some libraries. I don't really know, though. Try following the HOWTO in leech's sig first. It's specific to Ubuntu, so you may have some more luck following that one than the one you posted. If that doesn't work, I'll help you track down any libs you might have missed.

---

### Post by The Iron Curtain on 2006-12-02
> **diepruis said:**
> You might be missing some libraries. I don't really know, though. Try following the HOWTO in leech's sig first. It's specific to Ubuntu, so you may have some more luck following that one than the one you posted. If that doesn't work, I'll help you track down any libs you might have missed.
Okay, I went to leech's sig site and it was for Platinum, but I only have the original. However, there was a l[ink to a site]("http://icculus.org/~ravage/nwn/") that did Original. I followed the [FAQ]("http://icculus.org/~ravage/nwn/faq.html") and when I ran ./nwn_129_final.run, I got this:

```

dfoer@dfoer-laptop:~/Desktop/Downloads$ sudo ./nwn_129_final.run
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................
/home/dfoer/.setup7962: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
dfoer@dfoer-laptop:~/Desktop/Downloads$



```

I think it is a library problem. Can you help me?

EDIT: I found the system requirements on the FAQ. Can you help me decipher some of it? I think it might be the problem.

```

Linux 2.2 kernel or higher
glibc-2.1 or higher
ISO 9660 CDROM file system support
Microsoft Joilet CDROM extensions
570MB free in /tmp or $TMPDIR for data extraction
1.7GB minimum free space for the installed game
Your Neverwinter Nights CDROMs.

```

---

### Post by diepruis on 2006-12-03
> **The Iron Curtain said:**
> 
```

dfoer@dfoer-laptop:~/Desktop/Downloads$ sudo ./nwn_129_final.run
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................
/home/dfoer/.setup7962: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
dfoer@dfoer-laptop:~/Desktop/Downloads$

```


Looks like it's searching for the GTK libraries. You probably have version 2 installed, but NWN's installer wants version one. Fixing this should be easy, all we need to do is find the libraries it wants and install them using apt-get or aptitude. I think this command should do the trick:

```

sudo aptitude install libgtk1.2

```

---

### Post by The Iron Curtain on 2006-12-03
O My God! Thank you so much! It worked! I learned some stuff in the process too!

However....for some reason, it won't run the english patch which has all of the words and letters. Here;s a pic of what's going on

---

### Post by The Iron Curtain on 2006-12-03
Here's some output from my terminal:

```

dfoer@dfoer-laptop:~$ nwn_129_english.run
bash: nwn_129_english.run: command not found
dfoer@dfoer-laptop:~$ cd Desktop/Downloads
dfoer@dfoer-laptop:~/Desktop/Downloads$ nwn_129_english.run
bash: nwn_129_english.run: command not found
dfoer@dfoer-laptop:~/Desktop/Downloads$ ./nwn_129_english.run
bash: ./nwn_129_english.run: Permission denied
dfoer@dfoer-laptop:~/Desktop/Downloads$ sudo ./nwn_129_english.run
Password:
sudo: ./nwn_129_english.run: command not found
dfoer@dfoer-laptop:~/Desktop/Downloads$

```

Honestly, I have no Idea what's going on. ](*,) 

Thank you so much for you help! :D

---

### Post by Alpha1Dash1 on 2006-12-03
Hi TIC, looks like you're just about there - the only thing you have left to do is to make the "nwn_129_english.run" file executable. Using the file browser, navigate to your Downlaods folder & bring up the properties of the file. On the permissions tab, check the "Owener execute" box (top left in the grid of 9 that you'll see). Then the following will work:

dfoer@dfoer-laptop:~/Desktop/Downloads$ ./nwn_129_english.run

Having changed the persissions, you could also just double click on the icon and select "run in terminal" too, but if any errors occur you'll loose them when the window closes.

---

### Post by Perfect Storm on 2006-12-03
the easier way is just **sh XXXXXXXX.run**

---

### Post by leech on 2006-12-03
Actually for the Original version, what you'll want to do is run the Ravage installer, then go to [www.liflg.org](www.liflg.org) and click on Downloads, Native and Neverwinter Nights.  There you'll see a file called nwn_1.66-english.update.run, that'll be the update (with a gui even) of the 1.66 update.  After that, you would probably want to download the 1.68 patch and just extract that over your nwn directory with file-roller.

[http://nwn.bioware.com/support/patch_linuxhotu168.html](http://nwn.bioware.com/support/patch_linuxhotu168.html) there is the link for the patch.

I would say it's almost worth just putting out the 30 bucks and getting the Diamond edition, (or 40 bucks if you want the Platinum, the only difference between the two is that Platinum comes with a nice thick manual (which if you have played D&D you probably won't need, and Diamond comes with the extra module Kingmaker.))

That way you get all the extra cool stuff that comes with the extra two (or three) campaigns, plus the installer in my HOW TO works with either Platinum or Diamond.  

At one point in time, I was emailing the guy who had created the install script and he said he would work on making the installer work with all versions, but then his website has disappeared, so I don't know where he is at the moment.

Leech

---

### Post by diepruis on 2006-12-03
> **The Iron Curtain said:**
> Here's some output from my terminal:

```

dfoer@dfoer-laptop:~$ nwn_129_english.run
bash: nwn_129_english.run: command not found
dfoer@dfoer-laptop:~$ cd Desktop/Downloads
dfoer@dfoer-laptop:~/Desktop/Downloads$ nwn_129_english.run
bash: nwn_129_english.run: command not found
dfoer@dfoer-laptop:~/Desktop/Downloads$ ./nwn_129_english.run
bash: ./nwn_129_english.run: Permission denied
dfoer@dfoer-laptop:~/Desktop/Downloads$ sudo ./nwn_129_english.run
Password:
sudo: ./nwn_129_english.run: command not found
dfoer@dfoer-laptop:~/Desktop/Downloads$

```

Honestly, I have no Idea what's going on. ](*,) 

Thank you so much for you help! :D

You can also do the following from the terminal:

```

chmod u+x nwn_129_english.run

```

Glad I could be some help ;)

---

### Post by The Iron Curtain on 2006-12-03
Thank you so much everybody! It worked! I installed the patches with no problems. I learned alot from this experience. Thank you.

---

### Post by cor2y on 2007-03-03
Just a quick FYI after pulling out my hair for most of a day i discovered the ravage install scripts didn't work with my discs (Neverwinter Nights collector Edition and seperate copies of HOTU and SOU) it refused to extract the files from both disc 1 and 2 of the original NWN , the massive 1.3gb official client worked as well as the Loki install scripts, i wish i had known the about the loki script first.

SO if the Ravage scripts don't work try the Loki ones and if those don't work then and only then download the massive Linux client from Bioware

---

### Post by Rahano on 2007-03-03
Ok, decieded to post here instead of starting a new thread.

I have nvwn gold and I wanted to install it to my linux. 
So I followed the instructions [HERE]("http://nwn.bioware.com/downloads/linuxclient.html#nwngoldinstall") and when I run the Dmclient or NVM it just says error in the terminal and exits out.

---

### Post by cor2y on 2007-03-03
What is the exact error ?

---

### Post by Rahano on 2007-03-03
All it tells me is error. and exits out.

Im really lost...

---

### Post by cor2y on 2007-03-04
try launching from the terminal
cd to the directory NWN is installed in and type
> 
./fixinstall

Next type
> 
./nwn


When it crashes a error should be reported in the terminal let me know what it is.

---

### Post by Rahano on 2007-03-04
When I do fixinstall from the window, it runs in the terminal.

But when I do ./fixinstall it tells me that Im missing the ambiant(sp) files...

---

### Post by cor2y on 2007-03-04
then it wasn't extracted using the method at bioware.

A way to fix this is to move the relevant zip files from off the cd.
to a local directory and extract from there to whatever destination folder you chose.
If that doesn't work then try the samething using vmware server with a windows install (theres a how to in Tutorial section) and samba (again a tutorial is located there)
For some reason the zip files are not being extracted fully.

If that fails then there is the large linux client.
All you need for that one is the zip files from the expansion and your serial keys.

---

### Post by Blackdropbear on 2010-06-26
On change of scene entry into Luskan I get the following error.


desktop:~/nwn$ ./nwn
*** glibc detected *** ./nwmain: free(): invalid pointer: 0x0f9fd428 ***
======= Backtrace: =========
/lib32/libc.so.6(+0x6c231)[0xf742e231]
/lib32/libc.so.6(+0x6dab8)[0xf742fab8]
/lib32/libc.so.6(cfree+0x6d)[0xf7432b9d]
./nwmain(__builtin_delete+0x22)[0x85f2ba6]
./nwmain[0x80a85ea]
./nwmain[0x82b1c38]
./nwmain[0x82b1f81]
./nwmain[0x82ad51e]
./nwmain[0x82b3e78]
./nwmain(SDL_SetVideoMode+0x6de)[0x804fdd6]
/lib32/libc.so.6(__libc_start_main+0xe6)[0xf73d8bd6]
./nwmain(AIL_WAV_info+0x39)[0x804f851]
======= Memory map: ========
08048000-0862c000 r-xp 00000000 08:05 232681                             /home/wellington/nwn/nwmain
0862c000-087ac000 rwxp 005e3000 08:05 232681                             /home/wellington/nwn/nwmain
087ac000-0e0b3000 rwxp 00000000 00:00 0 
0e4dc000-133d0000 rwxp 00000000 00:00 0                                  [heap]
ef3c1000-f158a000 rwxp 00000000 00:00 0 
f1640000-f1840000 rwxs 6f982000 00:05 4644                               /dev/nvidia0
f1840000-f1b41000 rwxp 00000000 00:00 0 
f1b41000-f2b42000 rwxs 1491d000 00:05 4644                               /dev/nvidia0
f2b42000-f2b8d000 rwxp 00000000 00:00 0 
f2c2c000-f2ceb000 rwxp 00000000 00:00 0 
f2d9d000-f2e19000 rwxp 00000000 00:00 0 
f3500000-f3521000 rwxp 00000000 00:00 0 
f3521000-f3600000 ---p 00000000 00:00 0 
f365e000-f3724000 rwxp 00000000 00:00 0 
f3766000-f3867000 rwxp 00000000 00:00 0 
f3867000-f3a67000 rwxs 5e033000 00:05 4644                               /dev/nvidia0
f3c2a000-f3ceb000 rwxp 00000000 00:00 0 
f3cec000-f3d2c000 rwxs dff7d000 00:05 4644                               /dev/nvidia0
f3d2c000-f422c000 rwxs d0000000 00:05 4644                               /dev/nvidia0
f422c000-f43ed000 rwxp 00000000 00:00 0 
f4427000-f4527000 rwxs a2875000 00:05 4644                               /dev/nvidia0
f4527000-f4628000 rwxs ca5ac000 00:05 4644                               /dev/nvidia0
f4628000-f468c000 rwxp 00000000 00:05 1211                               /dev/zero
f468c000-f46ae000 rwxs 00000000 00:04 0                                  /SYSV00000000 (deleted)
f46ae000-f46af000 rwxp 00000000 00:00 0 
f470f000-f4710000 rwxp 00000000 00:00 0 
f4710000-f4711000 rwxs 00000000 00:04 97484949                           /SYSV00000000 (deleted)
f4711000-f4712000 rwxs 00000000 00:04 2097206                            /SYSV00000000 (deleted)
f4712000-f4713000 rwxs 00000000 00:04 2785351                            /SYSV00000000 (deleted)
f4713000-f4714000 rwxs 00000000 00:04 55378037                           /SYSV00000000 (deleted)
f4714000-f4715000 rwxs 00000000 00:04 55443572                           /SYSV00000000 (deleted)
f4715000-f4716000 rwxs 00000000 00:04 67371140                           /SYSV00000000 (deleted)
f4716000-f4717000 rwxs 00000000 00:04 69632142                           /SYSV00000000 (deleted)
f4717000-f4718000 rwxs 00000000 00:04 72122418                           /SYSV00000000 (deleted)
f4718000-f471c000 rwxs 4e5af000 00:05 4644                               /dev/nvidia0
f471c000-f471d000 rwxs dffbd000 00:05 4644                               /dev/nvidia0
f471d000-f471e000 ---p 00000000 00:00 0 
f471e000-f4f1e000 rwxp 00000000 00:00 0 
f4f1e000-f4f1f000 ---p 00000000 00:00 0 
f4f1f000-f5745000 rwxp 00000000 00:00 0 
f5745000-f5754000 r-xp 00000000 08:05 336708                             /home/wellington/nwn/miles/mssdsp.flt
f5754000-f5758000 rwxp 0000e000 08:05 336708                             /home/wellington/nwn/miles/mssdsp.flt
f5758000-f5759000 rwxp 00000000 00:00 0 
f5759000-f5763000 r-xp 00000000 08:05 336710                             /home/wellington/nwn/miles/msssoft.m3d
f5763000-f5765000 rwxp 00009000 08:05 336710                             /home/wellington/nwn/miles/msssoft.m3d
f5765000-f5769000 rwxp 00000000 00:00 0 
f5769000-f577f000 r-xp 00000000 08:05 336709                             /home/wellington/nwn/miles/mssmp3.asi
f577f000-f5786000 rwxp 00015000 08:05 336709                             /home/wellington/nwn/miles/mssmp3.asi
f5786000-f57eb000 rwxp 00000000 00:00 0 
f57eb000-f57ec000 rwxs 7018b000 00:05 4644                               /dev/nvidia0
f57ec000-f5bae000 rwxp 00000000 00:00 0 
f5bae000-f5baf000 ---p 00000000 00:00 0 
f5baf000-f6414000 rwxp 00000000 00:00 0 
f6414000-f6418000 r-xp 00000000 08:05 21152                              /usr/lib32/libXdmcp.so.6.0.0
f6418000-f6419000 r-xp 00003000 08:05 21152                              /usr/lib32/libXdmcp.so.6.0.0
f6419000-f641a000 rwxp 00004000 08:05 21152                              /usr/lib32/libXdmcp.so.6.0.0
f641a000-f641b000 rwxp 00000000 00:00 0 
f641b000-f641d000 r-xp 00000000 08:05 21144                              /usr/lib32/libXau.so.6.0.0
f641d000-f641e000 r-xp 00001000 08:05 21144                              /usr/lib32/libXau.so.6.0.0
f641e000-f641f000 rwxp 00002000 08:05 21144                              /usr/lib32/libXau.so.6.0.0
f641f000-f6437000 r-xp 00000000 08:05 21148                              /usr/lib32/libxcb.so.1.1.0
f6437000-f6438000 r-xp 00017000 08:05 21148                              /usr/lib32/libxcb.so.1.1.0
f6438000-f6439000 rwxp 00018000 08:05 21148                              /usr/lib32/libxcb.so.1.1.0
f6439000-f6456000 r-xp 00000000 08:05 592                                /usr/lib32/libgcc_s.so.1
f6456000-f6457000 r-xp 0001c000 08:05 592                                /usr/lib32/libgcc_s.so.1
f6457000-f6458000 rwxp 0001d000 08:05 592                                /usr/lib32/libgcc_s.so.1
f6458000-f6541000 r-xp 00000000 08:05 554                                /usr/lib32/libstdc++.so.6.0.13
f6541000-f6542000 ---p 000e9000 08:05 554                                /usr/lib32/libstdc++.so.6.0.13
f6542000-f6546000 r-xp 000e9000 08:05 554                                /usr/lib32/libstdc++.so.6.0.13
f6546000-f6547000 rwxp 000ed000 08:05 554                                /usr/lib32/libstdc++.so.6.0.13
f6547000-f654e000 rwxp 00000000 00:00 0 
f654e000-f6550000 r-xp 00000000 08:05 7352                               /lib32/libdl-2.11.1.so
f6550000-f6551000 r-xp 00001000 08:05 7352                               /lib32/libdl-2.11.1.so
f6551000-f6552000 rwxp 00002000 08:05 7352                               /lib32/libdl-2.11.1.so
f6552000-f6553000 rwxp 00000000 00:00 0 
f6553000-f666c000 r-xp 00000000 08:05 21143                              /usr/lib32/libX11.so.6.3.0
f666c000-f666d000 r-xp 00118000 08:05 21143                              /usr/lib32/libX11.so.6.3.0
f666d000-f666f000 rwxp 00119000 08:05 21143                              /usr/lib32/libX11.so.6.3.0
f666f000-f6670000 rwxp 00000000 00:00 0 
f6670000-f667e000 r-xp 000Aborted

---

### Post by Blackdropbear on 2010-06-26
Having a stack dump each time I try to enter Luskan - dump below. Any ideas ?

[email]wellington@wellington-desktop:~/.Games[/email]/nwn$ ./nwn
*** glibc detected *** ./nwmain: free(): invalid pointer: 0xec3526f0 ***
======= Backtrace: =========
/lib32/libc.so.6(+0x6c231)[0xf743d231]
/lib32/libc.so.6(+0x6dab8)[0xf743eab8]
/lib32/libc.so.6(cfree+0x6d)[0xf7441b9d]
./nwmain(__builtin_delete+0x22)[0x85f2ba6]
./nwmain[0x80a85ea]
./nwmain[0x82b1c38]
./nwmain[0x82b1f81]
./nwmain[0x82ad51e]
./nwmain[0x82b3e78]
./nwmain(SDL_SetVideoMode+0x6de)[0x804fdd6]
/lib32/libc.so.6(__libc_start_main+0xe6)[0xf73e7bd6]
./nwmain(AIL_WAV_info+0x39)[0x804f851]
======= Memory map: ========
08048000-0862c000 r-xp 00000000 08:05 273800                             /home/wellington/.Games/nwn/nwmain
0862c000-087ac000 rwxp 005e3000 08:05 273800                             /home/wellington/.Games/nwn/nwmain
087ac000-0e0b3000 rwxp 00000000 00:00 0 
0ee6d000-0fc70000 rwxp 00000000 00:00 0                                  [heap]
e5500000-e55ea000 rwxp 00000000 00:00 0 
e55ea000-e5600000 ---p 00000000 00:00 0 
e5600000-e56ff000 rwxp 00000000 00:00 0 
e56ff000-e5700000 ---p 00000000 00:00 0 
e5700000-e58fb000 rwxp 00000000 00:00 0 
e58fb000-e5900000 ---p 00000000 00:00 0 
e5900000-e59ff000 rwxp 00000000 00:00 0 
e59ff000-e5a00000 ---p 00000000 00:00 0 
e5a00000-e5ac1000 rwxp 00000000 00:00 0 
e5ac1000-e5b00000 ---p 00000000 00:00 0 
e5b00000-e5bee000 rwxp 00000000 00:00 0 
e5bee000-e5c00000 ---p 00000000 00:00 0 
e5c00000-e5cc5000 rwxp 00000000 00:00 0 
e5cc5000-e5d00000 ---p 00000000 00:00 0 
e5d00000-e5df9000 rwxp 00000000 00:00 0 
e5df9000-e5e00000 ---p 00000000 00:00 0 
e5e00000-e5ee2000 rwxp 00000000 00:00 0 
e5ee2000-e5f00000 ---p 00000000 00:00 0 
e5f00000-e5ff1000 rwxp 00000000 00:00 0 
e5ff1000-e6000000 ---p 00000000 00:00 0 
e60e6000-e62e8000 rwxp 00000000 00:00 0 
e62e8000-e64e8000 rwxs cbb4e000 00:05 4644                               /dev/nvidia0
e64e8000-e6800000 rwxp 00000000 00:00 0 
e6800000-e68d2000 rwxp 00000000 00:00 0 
e68d2000-e6900000 ---p 00000000 00:00 0 
e69fb000-e7500000 rwxp 00000000 00:00 0 
e7500000-e7700000 rwxs 107901000 00:05 4644                              /dev/nvidia0
e7700000-e77f1000 rwxp 00000000 00:00 0 
e77f1000-e7800000 ---p 00000000 00:00 0 
e78fe000-e7e00000 rwxp 00000000 00:00 0 
e7e00000-e7ed6000 rwxp 00000000 00:00 0 
e7ed6000-e7f00000 ---p 00000000 00:00 0 
e7f00000-e7ffb000 rwxp 00000000 00:00 0 
e7ffb000-e8000000 ---p 00000000 00:00 0 
e8000000-e80d6000 rwxp 00000000 00:00 0 
e80d6000-e8100000 ---p 00000000 00:00 0 
e8100000-e81d6000 rwxp 00000000 00:00 0 
e81d6000-e8200000 ---p 00000000 00:00 0 
e8200000-e82d6000 rwxp 00000000 00:00 0 
e82d6000-e8300000 ---p 00000000 00:00 0 
e8300000-e83d6000 rwxp 00000000 00:00 0 
e83d6000-e8400000 ---p 00000000 00:00 0 
e8400000-e84ab000 rwxp 00000000 00:00 0 
e84ab000-e8500000 ---p 00000000 00:00 0 
e8500000-e85d6000 rwxp 00000000 00:00 0 
e85d6000-e8600000 ---p 00000000 00:00 0 
e8600000-e86ab000 rwxp 00000000 00:00 0 
e86ab000-e8700000 ---p 00000000 00:00 0 
e87fe000-e8e00000 rwxp 00000000 00:00 0 
e8e00000-e8ed6000 rwxp 00000000 00:00 0 
e8ed6000-e8f00000 ---p 00000000 00:00 0 
e8f00000-e8fd6000 rwxp 00000000 00:00 0 
e8fd6000-e9000000 ---p 00000000 00:00 0 
e9000000-e90d9000 rwxp 00000000 00:00 0 
e90d9000-e9100000 ---p 00000000 00:00 0 
e91a4000-e9749000 rwxp 00000000 00:00 0 
e9afe000-e9bff000 rwxp 00000000 00:00 0 
e9d00000-e9dfd000 rwxp 00000000 00:00 0 
e9dfd000-e9e00000 ---p 00000000 00:00 0 
e9e00000-e9eb0000 rwxp 00000000 00:00 0 
e9eb0000-e9f00000 ---p 00000000 00:00 0 
e9f00000-ea100000 rwxp 00000000 00:00 0 
ea100000-ea1f6000 rwxp 00000000 00:00 0 
ea1f6000-ea200000 ---p 00000000 00:00 0 
ea200000-ea300000 rwxp 00000000 00:00 0 
ea300000-ea3fc000 rwxp 00000000 00:00 0 
ea3fc000-ea400000 ---p 00000000 00:00 0 
ea400000-ea500000 rwxp 00000000 00:00 0 
ea500000-ea6fc000 rwxp 00000000 00:00 0 
ea6fc000-ea700000 ---p 00000000 00:00 0 
ea700000-ea800000 rwxp 00000000 00:00 0 
ea943000-eaa00000 rwxp 00000000 00:00 0 
eaa00000-eaaea000 rwxp 00000000 00:00 0 
eaaea000-eab00000 ---p 00000000 00:00 0 
eab00000-eabf9000 rwxp 00000000 00:00 0 
eabf9000-eac00000 ---p 00000000 00:00 0 
eac00000-eacff000 rwxp 00000000 00:00 0 
eacff000-ead00000 ---p 00000000 00:00 0 
ead00000-eadfe000 rwxp 00000000 00:00 0 
eadfe000-eae00000 ---p 00000000 00:00 0 
eae00000-eb000000 rwxp 00000000 00:00 0 
eb000000-eb0ef000 rwxp 00000000 00:00 0 
eb0ef000-eb100000 ---p 00000000 00:00 0 
eb100000-eb200000 rwxp 00000000 00:00 0 
eb200000-eb400000 rwxp 00000000 00:00 0 
eb400000-eb5ff000 rwxp 00000000 00:00 0 
eb5ff000-eb600000 ---p 00000000 00:00 0 
eb600000-eb700000 rwxp 00000000 00:00 0 
eb700000-eb7db000 rwxp 00000000 00:00 0 
eb7db000-eb800000 ---p 00000000 00:00 0 
eb800000-eb8f6000 rwxp 00000000 00:00 0 
eb8f6000-eb900000 ---p 00000000 00:00 0 
eb900000-eb9f1000 rwxp 00000000 00:00 0 
eb9f1000-eba00000 ---p 00000000 00:00 0 
eba00000-ebc00000 rwxp 00000000 00:00 0 
ebc00000-ebdf4000 rwxp 00000000 00:00 0 
ebdf4000-ebe00000 ---p 00000000 00:00 0 
ebe00000-ec000000 rwxp 00000000 00:00 0 
ec000000-ec0ff000 rwxp 00000000 00:00 0 
ec0ff000-ec100000 ---p 00000000 00:00 0 
ec100000-ec1e9000 rwxp 00000000 00:00 0 
ec1e9000-ec200000 ---p 00000000 00:00 0 
ec200000-ec3df000 rwxp 00000000 00:00 0 
ec3df000-ec400000 ---p 00000000 00:00 0 
ec400000-ec4fd000 rwxp 00000000 00:00 0 
ec4fd000-ec500000 ---p 00000000 00:00 0 
ec600000-ec800000 rwxp 00000000 00:00 0 
ec800000-eca00000 rwxp 00000000 00:00 0 
eca00000-ecaab000 rwxp 00000000 00:00 0 
ecaab000-ecb00000 ---p 00000000 00:00 0 
ecb21000-ecbff000 rwxp 00000000 00:00 0 
ecbff000-edc00000 rwxs b86e1000 00:05 4644                               /dev/nvidia0
edc00000-edd00000 rwxp 00000000 00:00 0 
edd0e000-ede00000 rwxp 00000000 00:00 0 
ede00000-edf00000 rwxp 00000000 00:00 0 
edf59000-ee05a000 rwxp 00000000 00:00 0 
ee05a000-ee05b000 rwxs 00000000 00:04 105218110                          /SYSV00000000 (deleted)
ee100000-ee1a1000 rwxp 00000000 00:00 0 
ee1a1000-ee200000 ---p 00000000 00:00 0 
ee239000-ee600000 rwxp 00000000 00:00 0 
ee600000-ee6ff000 rwxp 00000000 00:00 0 
ee6ff000-ee700000 ---p 00000000 00:00 0 
ee771000-ee87d000 rwxp 00000000 00:00 0 
ee87d000-eea7d000 rwxs ca385000 00:05 4644                               /dev/nvidia0
eeb7e000-eec3f000 rwxp 00000000 00:00 0 
eec3f000-eed00000 rwxp 00000000 00:00 0 
eed00000-eedc1000 rwxp 00000000 00:00 0 
eedc1000-eee00000 ---p 00000000 00:00 0 
eee00000-eef00000 rwxp 00000000 00:00 0 
eef00000-eefe4000 rwxp 00000000 00:00 0 
eefe4000-ef000000 ---p 00000000 00:00 0 
ef05c000-ef05d000 rwxs 00000000 00:04 88375446                           /SYSV00000000 (deleted)
ef05d000-ef05e000 rwxs 00000000 00:04 97484949                           /SYSV00000000 (deleted)
ef05e000-ef05f000 rwxs 00000000 00:04 102334572                          /SYSV00000000 (deleted)
ef05f000-ef060000 rwxs 00000000 00:04 103710825                          /SYSV00000000 (deleted)
ef060000-ef0a0000 rwxs dff7d000 00:05 4644                               /dev/nvidia0
ef0a0000-ef5a0000 rwxs d0000000 00:05 4644                               /dev/nvidia0
ef5a0000-ef761000 rwxp 00000000 00:00 0 
ef79b000-ef89b000 rwxs b674d000 00:05 4644                               /dev/nvidia0
ef89b000-ef99c000 rwxs 04076000 00:05 4644                               /dev/nvidia0
ef99c000-efa00000 rwxp 00000000 00:05 1211                               /dev/zero
Aborted

---

