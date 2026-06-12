---
title: "Problems installing quake4"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by Yautja_Ender on 2006-01-06
Hey, i downloaded the linux installer, then started copying the .pk4 files from cd 1. Check

Then inserted the second cd and it told me
ERROR DISPLAYING FOLDER
"The folder contents could not be displayed."..."You do not have the permissions necessary to view the contents of "cdrom1"."

what to do? thanks

---

### Post by Wallakoala on 2006-01-06
[QUOTE=Yautja_Ender]Hey, i downloaded the linux installer, then started copying the .pk4 files from cd 1. Check

Then inserted the second cd and it told me
ERROR DISPLAYING FOLDER
"The folder contents could not be displayed."..."You do not have the permissions necessary to view the contents of "cdrom1"."

what to do? thanks[/QUOTE]

I ran into this exact problem. You have to type in ```
sudo -s
``` in the terminal and then you will be root. You will then be able to copy the files from the command line.

oh...btw have fun with quake 4. I really enjoyed it.

---

### Post by Yautja_Ender on 2006-01-06
I'm sorry, i did that but it said i still dont have permission... did you mean copying them to the folder using a console command this way... and also... how do i get back to being my real user name.

---

### Post by Wallakoala on 2006-01-06
ok so here is what you do:
in the terminal:
```
sudo -s
```
that makes you root
```
cp /cdrom/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base
```
(assuming that your cdrom drive is cdrom and you are copying the files to /usr/local/games/quake4/q4base)
this takes a while since the files are very big.
Do that for each disc.

if your terminal says 
```
root@ubuntu:~#

```
then to get back to being your user all you have to do is type
```
exit
```
and you will exit from being root

If this works, tell me

---

### Post by Wallakoala on 2006-01-06
Oh...I forgot to add something. 
Once you finish copying all of the files, you have to go into the directory where you copied them to and then type:
```

chmod 755 *.pk4

```

this will change the permissions on the files so that once its installed you can run "quake4" in the terminal without having to be root.

---

### Post by Yautja_Ender on 2006-01-06
It seems it isnt working here what i get:

root@ubuntu:~# cp /cdrom1/Setup/Data/q4base/pak002.pk4 /home/quake4/q4base
cp: cannot stat `/cdrom1/Setup/Data/q4base/pak002.pk4': No such file or directory

^i tried this with several of the .pk4 files... no succes.... :(


hmmm... also tried: 
root@ubuntu:~# cp /cdrom/Setup/Data/q4base/pak005.pk4 /home/quake4/q4base
cp: cannot create regular file `/home/quake4/q4base': No such file or directory
notice i didnt specify the cdrom... thats what it gave me

---

### Post by Wallakoala on 2006-01-06
[QUOTE=Yautja_Ender]It seems it isnt working here what i get:

root@ubuntu:~# cp /cdrom1/Setup/Data/q4base/pak002.pk4 /home/quake4/q4base
cp: cannot stat `/cdrom1/Setup/Data/q4base/pak002.pk4': No such file or directory

^i tried this with several of the .pk4 files... no succes.... :(


hmmm... also tried: 
root@ubuntu:~# cp /cdrom/Setup/Data/q4base/pak005.pk4 /home/quake4/q4base
cp: cannot create regular file `/home/quake4/q4base': No such file or directory
notice i didnt specify the cdrom... thats what it gave me[/QUOTE]

I know your problem. Where did you copy the files from the first cd to? If you already have a folder that you made called quake4, then you have to go to the command line and change your directory to quake4 and then ```
mkdir q4base
```

A good place to put games is the directory /usr/local
What I did was this:
```
mkdir -p /usr/local/games/quake4/q4base
```
and then I used the method that I described earlier to copy the files from the cds. If you want the quake 4 directory to be somewhere else all you have to do is just do ```
mkdir -p
``` followed by the path to the place where you want to have the files. For example if I wanted it to be in my home directory I would type:
```
mkdir -p /home/walla/quake4/q4base
```
and then I would copy the files off the cd like this:
```
cp /cdrom/Setup/Data/q4base/*.pk4 /home/walla/quake4/q4base
```

hope this helps

---

### Post by Yautja_Ender on 2006-01-06
ok so far i can copy the files to the default usr/local/quake4/q4base
cant send them directly to the folder i set the installer up on but ill prob just try and copy and paste them.... thanks so far :) hopefully this will work

---

### Post by Wallakoala on 2006-01-06
[QUOTE=Yautja_Ender]ok so far i can copy the files to the default usr/local/quake4/q4base
cant send them directly to the folder i set the installer up on but ill prob just try and copy and paste them.... thanks so far :) hopefully this will work[/QUOTE]

when they are done copying, do the following:
 1) if you have the quake4 installer downloaded, copy it to /usr/local/games/quake4
2) then, 
```
cd /usr/local/games/quake4/q4base
sudo chmod 755 *.pk4
```
3) run the installer:
```
cd /usr/local/games/quake4
sudo sh *insert name of installer here*

```
Then the installer will run and you will be set

---

### Post by Yautja_Ender on 2006-01-06
Ok i think i did everything right but heres what happend when i tried to run it from the root:

root@ubuntu:~#  sh quake4-linux-1.0.6.x86.run
Verifying archive integrity... All good.
Uncompressing Quake 4 (TM).....................................


(then alot of shit in between)


ERROR: SDL_SetVideoMode failed: Couldn't find matching GLX visual
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual
root@ubuntu:/usr/local/games/quake4/q4base#

---

### Post by Yautja_Ender on 2006-01-06
got it working!!! yay... thanks W

---

### Post by Yautja_Ender on 2006-01-06
Working... Unfortunately the sound is crap... anyway to fix this?

---

