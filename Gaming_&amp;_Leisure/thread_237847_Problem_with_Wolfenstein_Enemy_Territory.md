---
title: "Problem with Wolfenstein Enemy Territory"
date: 2006-08-16
forum: Gaming &amp; Leisure
---

### Post by BongoBob on 2006-08-16
Well I downloaded and installed the latest Linux version of Enemy Territory, but it doesn't seem to want to work. It does not save my profile. Every time I start it, it makes me make a new profile, and when I go to the profiles menu, it doesn't show up, nor any other one I've made. Also, when I try to join a game, it dooesn't download anything. It says Downloading 0%, then go to the next thing, and it just loops until I hit escape.

Any help would be much appreciated.

---

### Post by FenrisAbraxas on 2006-08-16
> **BongoBob said:**
> Well I downloaded and installed the latest Linux version of Enemy Territory, but it doesn't seem to want to work. It does not save my profile. Every time I start it, it makes me make a new profile, and when I go to the profiles menu, it doesn't show up, nor any other one I've made. Also, when I try to join a game, it dooesn't download anything. It says Downloading 0%, then go to the next thing, and it just loops until I hit escape.

Any help would be much appreciated.

Check the permissions of ~user/.etwolf and look at the folder content (there should be a profile folder inside the folder of each mod, etpub, etpro, jaymod etc)

---

### Post by BongoBob on 2006-08-16
And how would I go about checking the permissions.

Sorry, I'm still pretty new to linux.

---

### Post by Matt Yun on 2006-08-16
to check permissions:

ls -la ~/.etwolf

---

### Post by BongoBob on 2006-08-17
Ok, when I do that, it gives me this:

```
bongobob@RaptorBandito:~$ ls -la ~/.etwolf
total 16
drwxr-xr-x  4 root     root     4096 2006-08-15 23:12 .
drwxr-xr-x 34 bongobob bongobob 4096 2006-08-16 13:31 ..
drwxr-xr-x  2 root     root     4096 2006-08-15 23:12 etmain
drwxr-xr-x  2 root     root     4096 2006-08-15 23:12 pb
```

---

### Post by crane on 2006-08-17
> **BongoBob said:**
> Ok, when I do that, it gives me this:

```
bongobob@RaptorBandito:~$ ls -la ~/.etwolf
total 16
drwxr-xr-x  4 root     root     4096 2006-08-15 23:12 .
drwxr-xr-x 34 bongobob bongobob 4096 2006-08-16 13:31 ..
drwxr-xr-x  2 root     root     4096 2006-08-15 23:12 etmain
drwxr-xr-x  2 root     root     4096 2006-08-15 23:12 pb
```

You have two options.
One is term.
IN terminal type:
sudo chown -R bongobob:bongobob ~/.etwolf

Or you can type:
sudo nautilus
Then when the file browser opens, navigate to your home directory.
then hit ctrl h to show hidden files. Now right click on the .etwolf folder and select properties. Then change the owner from there. Make sure you change the permissions of all the files in the folder as well.
The first method would be quicker. The second would be more familiar to some one not used to linux but used to windows.

---

### Post by BongoBob on 2006-08-17
Thank you very much. That solved the problem with the profiles and the downloads, but now after it downloads any neccesary files, it freezes on the awaiting gamestate message. I'm on a router, do I need to forward any ports?

EDIT: I ran it through the terminal in windowed mode and this is what it gave me in the terminal:

```
----- finished R_Init -----
Sys_LoadDll(/home/bongobob/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/bongobob/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bongobob/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae48ff40
Sys_LoadDll(ui) succeeded!
Sys_LoadDll(/home/bongobob/.etwolf/etmain/cgame.mp.i386.so)...
Sys_LoadDll(/home/bongobob/.etwolf/etmain/cgame.mp.i386.so) failed:
"/home/bongobob/.etwolf/etmain/cgame.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/cgame.mp.i386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0xa927a7d0
Sys_LoadDll(cgame) succeeded!
LOADING... collision map
Received signal 11, exiting...
Shutdown tty console
```

---

### Post by MaximB on 2006-08-17
I have other problem...very silly one
I've downloaded the linux client but I didn't managed to install it
I type ./ or ./file name or other combinations but nothing work
how to install ?

---

### Post by BongoBob on 2006-08-17
Go to the directory in the terminal and type sh *filename here*.

---

### Post by ZylGadis on 2006-08-17
If you guys stop installing stuff as root, you won't have permission problems. Simple as that. Why do you need sudo if you are a single user, or if no other user will play ET (or whatever you are installing)?

So, to the post above mine: it's not sudo sh filename, it is sh filename.

As to the timeout thing - you don't need to forward ports. I am behind a NAT router, and I play ET without problems. Everything in the terminal paste seems fine, too. There obviously are communication problems somewhere, but again, you don't need to forward ports as all connections are initiated from an ET client to an ET server. I'd try a different server, or see if the router does not screw up the connection.

---

### Post by BongoBob on 2006-08-17
Sorry, didn't realize that. You could have made that sound less harsh, but thanks for the advice.

How would I go about uninstalling it, as I would like to try to reinstall it without sudo and see if that fixes everything.

---

### Post by patrick295767 on 2006-08-17
> **BongoBob said:**
> Well I downloaded and installed the latest Linux version of Enemy Territory, but it doesn't seem to want to work. It does not save my profile. Every time I start it, it makes me make a new profile, and when I go to the profiles menu, it doesn't show up, nor any other one I've made. Also, when I try to join a game, it dooesn't download anything. It says Downloading 0%, then go to the next thing, and it just loops until I hit escape.

Any help would be much appreciated.

By the way, has someone a good link to download freely the game ?

Thanks 

Pat'

---

### Post by BongoBob on 2006-08-17
[www.filefront.com](www.filefront.com) is where I got it.

---

### Post by Mongoose on 2006-08-18
If you ever have problems with 'mod fighting' this script will help:

```
#!/bin/sh
touch ~/.etwolf/etmain/profiles/*/etconfig.cfg
rm -f ~/.etwolf/*/profiles/*/profile.pid
cd /opt/games/enemy-territory/
/opt/games/enemy-territory/et.x86
```

I'm not sure if that's even still needed.  'Back in the day' it was, and I never quit using it.  =)

---

### Post by User_Program on 2006-08-18
> **patrick295767 said:**
> By the way, has someone a good link to download freely the game ?

Thanks 

Pat'


I use 3d gamers [http://www.3dgamers.com/games/wolfensteinet/downloads/](http://www.3dgamers.com/games/wolfensteinet/downloads/)

---

### Post by topsites on 2007-06-27
> **ZylGadis said:**
> If you guys stop installing stuff as root, you won't have permission problems. Simple as that. Why do you need sudo if you are a single user, or if no other user will play ET (or whatever you are installing)?

So, to the post above mine: it's not sudo sh filename, it is sh filename.

Yeah "Error /usr/local/bin does not have user write access"

That why we resort to sudo

---

