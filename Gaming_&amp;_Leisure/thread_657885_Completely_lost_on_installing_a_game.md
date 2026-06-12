---
title: "Completely lost on installing a game"
date: 2008-01-04
forum: Gaming &amp; Leisure
---

### Post by DanielJackins on 2008-01-04
I am attempting to install Regnum Online but none of the guides I've managed to find seem to work. One says to just run the ROlauncher but I can't double click it, nothing happens.

---

### Post by RomeReactor on 2008-01-04
Hi. Open a terminal (Applications->Accessories->Terminal) and change directory to where you have the rolauncher file. For example, I have it in a hidden folder called **.Games** in my home folder, so I would do:
```
cd .Games
```
then to run the game:
```
./rolauncher
```

Where do you have the file? bear in mind that after launching the game it will start to download the necessary files to run, so it's a good idea to have a dedicated folder just for the game.

---

### Post by DanielJackins on 2008-01-04
It is in my home directory in a folder called Regnum. Here is what it gave me when I tried to do what you told me;

*** glibc detected *** ./rolauncher: munmap_chunk(): invalid pointer: 0x08653920 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb782b92b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7737961]
./rolauncher[0x817613d]
./rolauncher[0x8070b53]
./rolauncher[0x8065a7a]
./rolauncher[0x8067ed1]
./rolauncher[0x810074e]
./rolauncher[0x805c55e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb77d4050]
./rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========
08048000-0840e000 r-xp 00000000 08:01 2654500    /home/daniel/Regnum/rolauncher
0840e000-0844b000 rw-p 003c6000 08:01 2654500    /home/daniel/Regnum/rolauncher
0844b000-08663000 rw-p 0844b000 00:00 0          [heap]
b5e71000-b5efc000 r--p 00000000 08:01 2968552    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5efc000-b5efe000 r-xp 00000000 08:01 2868540    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5efe000-b5eff000 rw-p 00001000 08:01 2868540    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5eff000-b5f05000 r--s 00000000 08:01 12140629   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5f05000-b5f08000 r--s 00000000 08:01 12142477   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5f08000-b5f0c000 r--s 00000000 08:01 12142320   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5f0c000-b5f0d000 r--s 00000000 08:01 12141746   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b5f0d000-b5f0e000 r--s 00000000 08:01 12141744   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5f0e000-b5f11000 r--s 00000000 08:01 12141688   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5f11000-b5f12000 r--s 00000000 08:01 12141686   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5f12000-b5f18000 r--s 00000000 08:01 12141126   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5f18000-b5f1a000 r--s 00000000 08:01 12141684   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5f1a000-b5f22000 r--s 00000000 08:01 12141618   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5f22000-b5f28000 r--s 00000000 08:01 12141616   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5f28000-b5f29000 r--s 00000000 08:01 12141508   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5f29000-b5f40000 r--s 00000000 08:01 12141212   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5f40000-b5f42000 r--s 00000000 08:01 12141481   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5f42000-b5f48000 r--s 00000000 08:01 12141472   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5f48000-b5f4c000 r--s 00000000 08:01 12140614   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5f4c000-b5f4e000 r--s 00000000 08:01 12141463   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5f4e000-b5f4f000 r--s 00000000 08:01 12143046   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b5f4f000-b5f50000 r--s 00000000 08:01 12143021   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5f50000-b5f51000 r--s 00000000 08:01 12146274   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b5f51000-b5f54000 r--s 00000000 08:01 12145702   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b5f54000-b5f57000 r--s 00000000 08:01 12143019   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5f57000-b5f5e000 r--s 00000000 08:01 9945089    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b5f5e000-b5f60000 r--s 00000000 08:01 12143002   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b5f60000-b5f61000 r--s 00000000 08:01 12143001   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b5f61000-b5f62000 r--s 00000000 08:01 12143000   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5f62000-b5f63000 r--s 00000000 08:01 12142999   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5f63000-b5f68000 r--s 00000000 08:01 12142998   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5f68000-b5f6d000 r--s 00000000 08:01 12142992   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b5f6d000-b5f6f000 r--s 00000000 08:01 12142991   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b5f6f000-b5f72000 r--s 00000000 08:01 12142988   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b5f72000-b5f73000 r--s 00000000 08:01 12142980   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5f73000-b5f74000 r--s 00000000 08:01 12145701   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b5f74000-b5f75000 r--s 00000000 08:01 12142976   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5f75000-b5f79000 r--s 00000000 08:01 12145685   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b5f79000-b5f7f000 r--s 00000000 08:01 12142972   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b5f7f000-b5f80000 r--s 00000000 08:01 12142971   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b5f80000-b5f88000 r--s 00000000 08:01 12143666   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b5f88000-b5f8c000 r--s 00000000 08:01 12145682   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b5f8c000-b5f9d000 r-xp 00000000 08:01 2802057    /usr/lib/gtk-2.0/2.10.0/engines/libglide.so
b5f9d000-b5f9e000 rw-p 00010000 08:01 2802057    /usr/lib/gtk-2.0/2.10.0/engines/libglide.so
b5f9e000-b5f9f000 ---p b5f9e000 00:00 0 
b5f9f000-b679f000 rwxp b5f9f000 00:00 0 
b679f000-b67c0000 rw-p b679f000 00:00 0 
b67c0000-b67e2000 r--p 00000000 08:01 3162360    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
b67e2000-b67eb000 r-xp 00000000 08:01 8749142    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b67eb000-b67ed000 rw-p 00008000 08:01 8749142    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b67ed000-b67f5000 r-xp 00000000 08:01 8749146    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b67f5000-b67f7000 rw-p 00007000 08:01 8749146    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b67f7000-b680b000 r-xp 00000000 08:01 8749133    /lib/tls/i686/cmov/libnsl-2.6.1.so
b680b000-b680d000 rw-p 00013000 08:01 8749133    /lib/tls/i686/cmov/libnsl-2.6.1.so
b680d000-b680f000 rw-p b680d000 00:00 0 
b680f000-b6816000 r-xp 00000000 08:01 8749138    /lib/tls/i686/cmov/libnss_compat-2Aborted (core dumped)

---

### Post by RomeReactor on 2008-01-04
What video card do you have? please post the output of these commands:
```
sudo lshw -C display
```
and:
```
glxinfo | grep direct
```

---

### Post by DanielJackins on 2008-01-04
*-display               
       description: VGA compatible controller
       product: GeForce 6100 nForce 430
       vendor: nVidia Corporation
       physical id: e
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
daniel@daniel-desktop:~$ glxinfo | grep direct
direct rendering: Yes

---

### Post by RomeReactor on 2008-01-04
Are you running Ubuntu 32-bit, or 64? try running the game like this:
```
sh -c "cd /home/daniel/Regnum && MALLOC_CHECK_=0 ./rolauncher"
```

---

### Post by DanielJackins on 2008-01-04
I'm running 32 bit, and that worked.

Mind explaining what that code you just gave me means? And would there be any easier way of launching?

---

### Post by K.Mandla on 2008-01-04
(I'm just going to shift this to Gaming and Leisure, since it's a support request for a Linux native game. :) )

---

### Post by RomeReactor on 2008-01-04
The **sh -c** is to read the command from the string that follows, which first tells it to change directory and then execute the command; the MALLOC_CHECK_=0 is to skip checking for memory allocation errors, I think. You can also run it like you tried before, by changing directory:
```
cd ~/Regnum
```
and then running the launcher with the malloc parameter:
```
MALLOC_CHECK_=0 ./rolauncher
```
though doing these steps separately tends to dump all the files the game downloads to your home folder, instead of where you put it. You can make an entry in the menus: Right-click on the menus, select "Edit Menus", on the left highlight "Games" and on the right press "New Item"; then fill it out like this:

* Type: Application
* Name: Regnum Online
* Command: sh -c "cd /home/daniel/Regnum && MALLOC_CHECK_=0 ./rolauncher"
* Comment: (you can leave it blank if you want).

For the icon, search for images and save a small .jpg, or resize a larger one with Gimp.

If you want the launcher in your desktop, just drag it from the menus.

---

### Post by nefrin on 2008-05-22
I am having issues installing as well. Even running MALLOC_CHECK_=0 ./rolauncher, I am recieving Segementation Faults:

[  140.394728] rolauncher[6453]: segfault at 0 rip f780d06a rsp ffbc2fa8 error 6
[  149.759031] rolauncher[6461]: segfault at 0 rip f77e206a rsp ffb74d58 error 6

I am aware that this usually constitutes a RAM issue, as I have already replaced the RAM stick that was orginally causing my segfaults. 

I have also already gone through and tested each stick of RAM in my system one at a time trying to run the rolauncher, each recieves a Segfault, each one segfaults the MALLOC_CHECK

So I'm at a loss here. I am going to attempt to redownload the file in the event that it's been corrupted somehow, and give it another shot, but any info that could help me would be greatly appreciated. I would love to play Regnum online.

Hmmmm, just for S&G, I tried MALLOC_CHECK_=1 ./rolauncher, and got a response. still waiting for my account to catch up on the server, but I'm getting a login screen.

It worked. setting MALLOC_CHECK_=1 ./rolauncher for the install program allowed it to run fine and do the intial download and install. After that, just running the launcher that installs in the regnum folder works fine. Not sure why the segfaults kept popping up, but I'm around it now.

---

### Post by vmayer on 2008-06-27
I'm completely new to Ubuntu. I downloaded the installer for Regnum Online (32-bit linux version). I put it in ~/Regnum but I don't know what to do next! The new installer is an executable but by default it wants to open with Wine. I downloaded the native linux version so I think this is wrong.

How do I install??

---

### Post by jimmysheldon on 2008-06-30
i'm in the same situation as vmayer, so please someone help.

---

### Post by vmayer on 2008-06-30
Here's what you do:

Put the install file *RegnumOnlineInstall_32* (or 64) in ~/regnum    (short for /home/your_name/regnum).

To make it executable, open up Terminal and enter the following:
```
chmod +x ~/regnum/RegnumOnlineInstall_32
```
Then run the installer:
```
sh -c "cd ~/regnum && ./RegnumOnlineInstall_32"
```

It should be pretty simple from there.  If this works for you, send me a Thanks. -------------------------------------------------------------------------------------------------------------->

---

### Post by jimmysheldon on 2008-07-01
Cheers vmayer! Thanks has been given. Guess i'll see you Regnum!

---

### Post by h4mx0r on 2008-08-29
I followed the tip about malloc check however character creation screen is all garbled so I can't see right. Any clue how to fix that error?

---

### Post by damod on 2009-12-12
Thanks vmayer, I was lost untill I read your solution.

---

### Post by bomzy on 2009-12-27
Thx dude! I was stuck a bit here, until I found your post! Good to see Ubuntu'ers helping each other ;)

---

### Post by thebrother23 on 2010-01-15
Thanks mate. Very straightforward. Pity they didn't put these instructions on the Regnum site.

---

### Post by Apocalypse_Ant on 2011-07-26
You rock!
:guitar:
Works perfectly.

---

