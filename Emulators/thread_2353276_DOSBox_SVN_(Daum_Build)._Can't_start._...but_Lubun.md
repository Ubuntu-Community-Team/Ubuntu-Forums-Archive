---
title: "DOSBox SVN (Daum Build). Can't start. ...but Lubuntu worked?"
date: 2017-02-20
forum: Emulators
---

### Post by AnttiV on 2017-02-20
Okay. I'm officially out of ideas. What the heck I'm doing wrong?

I've been playing for a few days with my old laptop running Lubuntu 16.04/16.10 (I forgot if I upgraded it or not). Installed DOSBox via the software library and it works fine. But I've used the Daum build (from [http://ykhwong.x-y.net/](http://ykhwong.x-y.net/) ) on my windows machine before and wanted to try that. So I downloaded a build, unpacked it and tried to start it and it wouldn't launch. Never really figured out why, but after I made a .desktop file for it, it launched just fine and everything worked (albeit REALLY slow, because of the old laptop.)

However, now that I managed to bring my main linux machine online (it was borked for the longest time), running Xubuntu 16.10, I can't make that DOSBox run at all. No way. I can run the dosbox from software library just fine, but I can't manage to start the SVN build. Not with .desktop files, not running from a terminal, not straight just double-clicking on it. Nothing works.

All I get is a "bash: ./dosbox: No such file or directory" (from terminal) or Failed to execute file "dosbox". Failed to execute child process "/home/antti/DOSBox/dosbox" (No such file or directory) (when double-clicking from file manager). 

Well it obviously DOES exist since I can click it.. why can't I make it run? (and yes, I did chmod +x it first after extracting from the archive).


EDIT: I might've figured it out. Turns out my Xubuntu installation media was x86_64, which apparently in linux-terms means roughly "nothing whatsoever will work". I would've though that we'd figure out a way since it's 2017 and all, but... but what can you expect when setting up network filesharing between two linux computers is some 25 years behind the competition...

---

### Post by Keith_Helms on 2017-02-20
I'm running 64-bit Xubuntu 16.04 and Dosbox from the repositories works fine on my system.

---

### Post by tiar85 on 2017-03-13
It's not easy task to get DOSBox SVN Daum to work under -buntus.

It's been asked earlier, but the thread is now closed: [https://ubuntuforums.org/showthread.php?t=2115589](https://ubuntuforums.org/showthread.php?t=2115589)

I'm not sure if my guide will help you, but I'll post it here anyway, if somebody else will find it useful:

(It took me about four hours to get it working, and I needed to check some commands from other sources.) 

**-----**

To get DOSBox SVN Daum to run under Ubuntu (should work with other -buntus as well), you will have to do the following steps: 
 
1. Uninstall existing version of DOSBox, if you have any. 
 
2. Open Terminal and go to your ./home -directory and then type the command: 
 
    mkdir -p ~/bin 
 
3. Extract DOSBox SVN Daum to the directory you have created. 
 
4. Go to ./bin -directory and then type the command: 
 
    chmod u+x dosbox 
 
4. Make sure you have the following lines added to ./home/user/.profile -file: 
 
    if [ -d "$HOME/bin" ] ; then 
        PATH="$HOME/bin:$PATH" 
    fi 
 
5. Reboot the computer. You can also try typing the following command: 
 
    exec -l bash 
 
6. It should work now.

(In this guide, default path has been used, but it is always possible to configure it as one wishes. Another note: this works for single user.)

**-----**

Bonus: Getting DBGL to notice SVN Daum -build:

1. Open DBGL.
2. Go to "DOSBox version"-tab.
3. Click "Add version".
4. Type the following:

Title: DOSBox SVN Daum 20150125
Path: /home/user/bin
Config File: /home/user/bin/dosbox.conf
Mark just "Default" with "x".

5. Press "OK".

6. Go back to "Profiles"-tab.
7. Pick a game and click "Edit profile".
8. Choose "General"-tab.
9. Go to "Association" and "DOSBox Version".
10. Pick "DOSBox SVN Daum 20150125" and click "Set" next to the title.
11. Hit "OK".
12. Repeat steps 7 - 11 for each game you have.
13. Done!

---

### Post by deadflowr on 2017-03-13
*Thread moved to **Emulators**.*

---

### Post by AnttiV on 2017-11-27
Sorry to come back to an older thread, but I've not had time to play with this the whole year basically. Now that I have again, well...

> **tiar85 said:**
> It's not easy task to get DOSBox SVN Daum to work under -buntus.

Amen on that!  

> **tiar85 said:**
> 6. It should work now.

Well, unfortunately it doesn't. I did everything you said but all I get is:

```
antti@laptopxubuntu:~$ dosbox
bash: /home/antti/bin/dosbox: No such file or directory
antti@laptopxubuntu:~$ cd bin
antti@laptopxubuntu:~/bin$ dir
CAPTURE  dosbox       FONTS           glide2x.ovl    SAVE
DOCS     dosbox.conf  glide2x_emu.ovl  libglide2x.so  win9x-drv
antti@laptopxubuntu:~/bin$ ./dosbox
bash: ./dosbox: No such file or directory

```

So as the DOSBox has been made for 32bit builds, is there anything I can do to run it on a x86_64 build? I really don't want to install a whole separate OS for just one program, but the 0.74 DOSBox from the Software Library just isn't enough. You'd THINK that you'd be able to run a 32bit program on 64bit OS, since practically any other OS is capable of that.. 

so, is there anything I can do, besides installing a separate 32bit version of 'buntu?

---

### Post by AnttiV on 2017-11-27
OK. I got it to run, sort of. 

I bumped my accident into a thread discussing running another 32bit program on 64bit host.

From there I noticed that ```
ldd ./dosbox
``` produced only "this is not a dynamic executable" (or something along those lines).

so I proceeded with ```
[COLOR=#111111][FONT=Consolas]sudo apt-get install gcc-multilib[/FONT][/COLOR]
```

after which ldd produced results and I continued, line by line apt-get installing every missing library with :i386
libasound2, libtbb2, libdbus-1.3, libX11.6, libGL.1. (anyone doing this, note that libGL installs a metric ass-ton of dependencies, so make sure you have room on the HDD...)

After installing those, dosbox now runs and works beautifully... except it outputs no sound. in-emulator everything works, but I can't hear anything.

I suppose the 32bit libasound2 doesn't have an output anywhere?

---

### Post by mahen2 on 2018-04-13
Hi ! I'm trying to get it to work too :-) I tried building it but get the same issue as the guy/gal here : 
[https://github.com/aybe/dosbox-svn-daum/issues/1](https://github.com/aybe/dosbox-svn-daum/issues/1)
Building duganchen's fork is easier but I need multipass shaders support ;-)
Another possibility is to use DosBox through RetroArch, but it raises other issues...
Or maybe dosbox via wine ?!

---

