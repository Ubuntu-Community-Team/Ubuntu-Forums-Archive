---
title: "Unreal Tournement Error"
date: 2006-05-18
forum: Gaming &amp; Leisure
---

### Post by muffinhead on 2006-05-18
Hello, I recently installed Unreal Tournement Editors Choice edition DVD On Linux using the Included Linux Installer.

When I Go to Install it I am Presented with this error as soon as I start up the terminal :

   	 	 	 	 	 	 	 	  Error #1: /root/.setup12246: error while loading shared libraries: libgtk-1.2.so.0  
 cannot open shared object file: No such file or directory.

 
When I go to run the game via the terminal I get this error, and the game never starts up :

 
   	 	 	 	 	 	 	 	  Error #2: ./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
 

    	 	 	 	 	 	 	 	  Error #1 Occurs when I run the Linux Installer for UT2004, and error #2 occurs when I go to run the game from the terminal, and it fails to start, resulting in that error message from the terminal.
 
 

 Can anyone tell me what I have to do, or download, in order to get this game to work in ubuntu?

 
If anyone could help me, I'd really appreciate it, Thank You;)

 
I'm Very new to Linux, and am trying to learn as much as I can, and have absolutely no clue what I need to do, download, or configure.

---

### Post by bluevoodoo1 on 2006-05-18
Are you sure you need to be root to install it?

error one:
might need some libgtk packages, like this... 
[http://packages.ubuntulinux.org/breezy/libs/libgtk1.2](http://packages.ubuntulinux.org/breezy/libs/libgtk1.2) or
[http://packages.ubuntulinux.org/breezy/libdevel/libgtk1.2-dbg](http://packages.ubuntulinux.org/breezy/libdevel/libgtk1.2-dbg)

so perhaps...

```
sudo apt-get install libgtk1.2 libgtk1.2-dbg
```

error two:
```
sudo apt-get install libstdc++5
```

---

### Post by Wr8EYilK8Y on 2006-05-18
bluevoodoo1's right.  I got this same error, do what he said to do

---

### Post by muffinhead on 2006-05-19
Thanks, I got it to work, By the way, is there anyway to fire up the UT2004 map editor in Linux? I tried finding a way, so I could test some of the maps I made in windows, on Linux, to see if they maybe had a little performance gain running under Linux. Thanks once again if you can let me know;)

---

### Post by Wr8EYilK8Y on 2006-05-19
ut2004ed in the ut2004/system dir, if I recall correctly. I've got to remember to install the "XP only" maps using wine.

---

### Post by muffinhead on 2006-05-19
I know it's in the system directory, But I don't know how to start the map editor in Linux for Unreal Tournement 2004.

Could someone tell me how I can start the map editor in Linux on UT2004, or tell me the console command to do so, I am totally lost as how to open up the map editor in Linux.

If you can't use unrealed, or the map editor in Linux, Please let me know, so I don't waste my time Posting, Thank You;)

---

### Post by Harleen on 2006-05-20
You can't use the Unreal editor in Linux, so don't waste your time. :razz:
For UT2007 it is planned, that also the editor wil be running under Linux. But until then, you have to create your maps with Windows.

---

### Post by muffinhead on 2006-05-20
Thanks for replying, I'm glad you let me know, so I'm not sitting here wasting my time trying to load the editor.

Btw, once I create my maps in windows, and put them in the map folder on linux, how can I play them on Linux? I've never seen an option to load custom maps from within the game, I've always had to load them via the editor in windows, and since I can't use the editor in Linux, I'm totally stuck and confused.

I am asking this, since I can't use the editor in Linux to make/load/play my maps, is there another way I can load my custom maps to play under Linux.

I know this may not be the appropriate website/forum to ask this, but since my original question was about UT2004 and Ubuntu, I figured, hey why not knock of two bird with one stone;)

---

### Post by Wr8EYilK8Y on 2006-05-22
So UT2007 WILL have a Linux port? Sweet. Now to upgrade my computer.

EDIT: It loads them automatically into your maplist towards the bottom, I believe.

---

### Post by Eclipsor on 2006-06-06
Related question. Trying to get UT2k4 working. It was working fine after I installed it and installed the package mentioned above. However, I patched it with the latest patch. 3876 or something. And now I get this error when I try and run the game.

cameron@ubuntu:/usr/local/games/ut2004$ ./ut2004
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I've tried installing any packages that look like this. Thanks for any help.

---

### Post by BLTicklemonster on 2006-06-07
I think you can probably install wine and get unreal ed to work. At least you can with UT, not sure about 2k4.

---

### Post by juicemansam on 2006-06-08
[QUOTE=Eclipsor]Related question. Trying to get UT2k4 working. It was working fine after I installed it and installed the package mentioned above. However, I patched it with the latest patch. 3876 or something. And now I get this error when I try and run the game.

cameron@ubuntu:/usr/local/games/ut2004$ ./ut2004
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I've tried installing any packages that look like this. Thanks for any help.[/QUOTE]
Make sure that libSDL-1.2.so.0 exists in your UT's System directory. If it doesn't, you can either copy over your system's libSDL-1.2.so.0 into the System directory, or compile one of your own. If you compile one of your own, the library, after compiling will be in .lib/ directory within the SDL source tree (I forget if it's in src/ or lib/ or something like that). Compiling your own could probably speed things up if you optimize the library, but I really don't have data to back that assumption.

Also, make sure that you have your environment variable UT2004_DATA_PATH set to your System. I'm not sure if it's really necessary, but it doesn't hurt to have it set.

---

### Post by Eclipsor on 2006-06-08
[QUOTE=juicemansam]Make sure that libSDL-1.2.so.0 exists in your UT's System directory. If it doesn't, you can either copy over your system's libSDL-1.2.so.0 into the System directory, or compile one of your own. If you compile one of your own, the library, after compiling will be in .lib/ directory within the SDL source tree (I forget if it's in src/ or lib/ or something like that). Compiling your own could probably speed things up if you optimize the library, but I really don't have data to back that assumption.

Also, make sure that you have your environment variable UT2004_DATA_PATH set to your System. I'm not sure if it's really necessary, but it doesn't hurt to have it set.[/QUOTE]

Thanks for the reply. That file is in the system directory. Could you please elaborate on how to do that environment variable thing. Sorry. noob.

---

### Post by juicemansam on 2006-06-09
To set the variable, you can run "export UT2004_DATA_PATH=/usr/local/games/ut2004/System" in a terminal window. Then ins the same window, run ut2004, that way you can see any messages. I'm not sure, but I think the UT2004_DATA_PATH environment variable is very similar to LD_LIBRARY_PATH, but for UT2004. I don't have a working system to test that out, but I remember reading that it should be set (maybe from the install readme). Well, should the variable fix your UT2004 install, you can then make the variable permanent by adding it to one of the following files, /etc/profile, ~/.bashrc, ~/.bash_profile. I recommend adding it to ~/.bash_profile, unless other users will also play ut2004 under their user accounts, which would require the variable either set in each of their own .bash_profile's or in /etc/profile. That's what I would do, but there's probably other ways of setting it, such as a bash script that sets it just before calling the binary, such adding the export line in the file "ut2004" (I don't remember, but I think it's a script that calls ut2004-bin).

---

### Post by Eclipsor on 2006-06-09
Unfortunately this didn't help. Still get the same error. I just reinstalled the whole game aswell and used the patch from linux-gamers.

---

