---
title: "Wolfenstein Enemy Territory: 'Run.gz - not in gzip format'"
date: 2010-07-29
forum: Gaming &amp; Leisure
---

### Post by Masamune12003 on 2010-07-29
I've been trying to download and install Wolfenstein enemy territory from guides on the internet for the last few hours and to be honest I'm at my wits end, I cannot for the life of my figure out how to extract this file!
The only linux versions of Wolfenstein ET I can find download as run.gz and they cannot be opened by the built in archive app (Archive Roller?) and I know of no other apps that are able to work with this file system, I can't even find any evidence other than my own downloaded files that it even exists anywhere else.

What do I do?! ](*,)

---

### Post by 2Karl on 2010-07-29
open a terminal, go to the location of the zip file and type:

```

tar -xzvf run.gz

```

---

### Post by Masamune12003 on 2010-07-29
Same error- here's what it gives me.

Joe@joe:~/Desktop$ tar -xzvf EnemyTerritory.run.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

I've got Wolfenstein installed and running now through PlayDeb but the whole reason I wanted it was to install the True Combat Elite patch which isn't availabe through PlayDeb and is in the same format as the original ET download.

I just can't figure out why they have packaged it the way they have, it is making things sooo difficult, I'm sure people have managed to install this before but I have no idea how.
Any other ideas?

---

### Post by Technophobia on 2010-07-29
[http://ubuntuforums.org/showthread.php?t=1538809](http://ubuntuforums.org/showthread.php?t=1538809)


Linux doesn't care about extensions. Just run the file. It's a misleading file name that's all.


chmod +x ET_v2.60_Linux.run.gz; sudo ./ET_v2.60_Linux.run.gz

---

### Post by Masamune12003 on 2010-07-30
O.O I'm sure I'd already tried that, I remember ther MIlf and Cookies comment xD

Anyway, it seems to be working.

Thank you!

---

### Post by Masamune12003 on 2010-07-30
Okay I have both WolfET and TruCE installed on my computer with there items showing in the menu, WolfET will load with no problem but when I try to load TruCE the screen goes black before returning to desktop, I tried running it through Terminal and this is there error message I get.

> 
----- Sound Info -----
sound system is muted
    1 stereo
262144 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0xab6b7000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/joe/.etwolf/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/home/joe/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/joe/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so) failed:
"libstdc++.so.5: cannot open shared object file: No such file or directory"
Sys_LoadDll(ui) failed dlopen() completely!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: VM_Create on UI failed


Not sure what I've done wrong, followed the site instructions and those from the thread you linked.

Also I've tried running the mod from within WolfET but that just made WolfET quit to desktop.

---

### Post by Perfect Storm on 2010-07-30
Just check the output you paste here:
> "libstdc++.so.5: cannot open shared object file: No such file or directory"

Though libstdc++5 is obsolete and no longer available - you can find it in ubuntu earlier release: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
If you're running 64-bit you might want to get 'getlibs' to handle the libstdc++5 32-bit version.

---

### Post by Masamune12003 on 2010-07-30
Cheers :)

---

### Post by huexos on 2010-11-29
> **Technophobia said:**
> [http://ubuntuforums.org/showthread.php?t=1538809](http://ubuntuforums.org/showthread.php?t=1538809)


Linux doesn't care about extensions. Just run the file. It's a misleading file name that's all.


chmod +x ET_v2.60_Linux.run.gz; sudo ./ET_v2.60_Linux.run.gz


Works Excellent thx.

---

### Post by mnkymnky on 2011-12-11
BTW what all this means to people who are noob like me or afraid of the terminal is that you just need to change the file name from blahblahblah.run.gz to blahblahblah.run and then as long as permission is set for it to be executable just run it.

Also i had a problem installing TCE after ET because it says I don't have v2.60 enemy territory installed when I clearly do cause it runs fine.

discovered this command:
./nameoffile.run --noexec --keep
which works for this file anyway; it uncompresses the .run file so I can see all the files in it without trying to install anything.

im gonna try a manual install just putting the folder in place.

edit: putting the tcetest folder in place makes it show up in mods menu when running ET but when activating it or loading with TCE it crashed : sv couldnt create on UI or something

edit2: problem was just a missing link for me fix: sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
that fix will only work if you already have the c++ library installed. if you you don't then you would need to
 sudo apt-get install libstdc++.so.5, libstdc++.so.6
5 might not still be in the repositories since its old. just the newest version=6 should do if you cant get 5 also.

---

