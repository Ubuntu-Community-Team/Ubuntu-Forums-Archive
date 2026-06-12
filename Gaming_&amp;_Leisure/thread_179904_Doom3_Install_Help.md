---
title: "Doom3 Install Help"
date: 2006-05-21
forum: Gaming &amp; Leisure
---

### Post by flaak_monkey on 2006-05-21
I am trying to run the doom3-linux-1.3.1302.x86.run,  but when it comes to where to install it into a dierectory, the default one it click OK, but it says i do not have permission to write.

---

### Post by bluevoodoo1 on 2006-05-21
If you're trying to install it to a folder in your root directory, try using "sudo" in the command to install it.

---

### Post by _simon_ on 2006-05-21
Just change the directory to your home one :)

---

### Post by flaak_monkey on 2006-05-22
im confused?!?!

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=flaak_monkey]im confused?!?![/QUOTE]

The game will probably be installed in /usr/local/games, so use sudo to gain permission to install it there, for example...

```
sudo sh doom3-linux-1.3.1302.x86.run
```


(I think what _simon_ was suggesting was... If it is possible during the installation process, you might be able to change the directory to which is to be installed to--like your home folder--so you will have permissions to write there.)

---

### Post by flaak_monkey on 2006-05-22
[http://img.photobucket.com/albums/v639/axelrose223/Screenshot-1.png](http://img.photobucket.com/albums/v639/axelrose223/Screenshot-1.png)

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=flaak_monkey][http://img.photobucket.com/albums/v639/axelrose223/Screenshot-1.png](http://img.photobucket.com/albums/v639/axelrose223/Screenshot-1.png)[/QUOTE]

that's ok.

If you used... sudo sh doom3-linux-1.3.1302.x86.run -- it will install there
if you used... sh doom3-linux-1.3.1302.x86.run -- it won't install there

---

### Post by flaak_monkey on 2006-05-22
[QUOTE=bluevoodoo1]that's ok.

If you used... sudo sh doom3-linux-1.3.1302.x86.run -- it will install there
if you used... sh doom3-linux-1.3.1302.x86.run -- it won't install there[/QUOTE]


when i use the sudo it says there is no sh doom3-linux-1.3.1302.x86.run.

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=flaak_monkey]when i use the sudo it says there is no sh doom3-linux-1.3.1302.x86.run.[/QUOTE]


Can you paste in from the terminal window what exactly is happening?

---

### Post by flaak_monkey on 2006-05-22
[QUOTE=bluevoodoo1]Can you paste in from the terminal window what exactly is happening?[/QUOTE]

flaakmonkey@flaakmonkey:~$ sudo sh doom3-linux-1.3.1302.x86.run
Password:
sh: doom3-linux-1.3.1302.x86.run: No such file or directory
flaakmonkey@flaakmonkey:~$

---

### Post by bluevoodoo1 on 2006-05-22
Where is the file located? Desktop? home folder? Another folder? Are you installing this from a CD? 

How did you get the installer open before? Please give me as much detail as possible.

---

### Post by flaak_monkey on 2006-05-22
i have the actaul CDs. The .run thing you need for linux is on the desktop. i got it to open before by just clicking it. (it is set to execute.) but when it comes to that screen to install to a directory it wont let me.

---

### Post by bluevoodoo1 on 2006-05-22
OK 

```

cd ~/Desktop
sudo sh doom3-linux-1.3.1302.x86.run

```

---

### Post by flaak_monkey on 2006-05-22
i give up. its not working. thx anyways dude. :(

---

### Post by _simon_ on 2006-05-23
or you can open terminal, type sh then drag and drop the file from it's location into terminal. This will give you the exact location of it. - it's lazy but quick ;)

If you change the path to make the installation directory in your home directory then you shouldn't have an issue.

So instead of /usr/local/games/doom3 use /whatever/home/doom3

---

### Post by muffinhead on 2006-05-23
I may be able to help, I had the same problem with doom 3, and was able to figure it out.

If you've already downloaded the doom3-x86.run, or whatever it is off the net, all I did is open the nautilus file manager as root access with : 

gksudo nautilus, copy and paste the doom3-x86.run file in my root directory, then I double clicked it, a popup window came up and asked me whether I wanted to display the file, or Run it in a terminal, I chose run it in the terminal, and then I installed it.

Like I said, put the doom3-x86.run in your root directory, execute it by double clicking, and choose run in terminal, Install it, and you should be fine.

This worked for me on Breezy Badger 5.10 release of Ubuntu, I don't know if it will work with other versions Of ubuntu, but it's worth a try.

Hope I may of been of help;)

Btw, make sure you have read/write Privileges to wherever you install it to, or it won't let you install. I would also stick to the default directory for games, ie.. /usr/local/games/doom3

hope that helps, I didn't catch your last post in time, before I posted, so some of what I mentioned, you've might of already tried.

---

### Post by AngryKidJoe on 2006-06-08
```
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.1.2/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/akj/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

```

How do I fix that? I also noticed in the installer the DOOM 3 install option is grayed out.

---

### Post by beeldings on 2006-06-08
Did you read the ID Software [FAQ]("http://zerowing.idsoftware.com/linux/doom/") for Doom 3?

What you have to do next is copy the remaining .pk4 files from the installation CDs to your hard drive, and then run doom3. What I did to accomplish this was to insert and mount the CD and then copy the files to the Doom 3 directory from a terminal. First, insert disc one. Once disc one is mounted, open up a terminal and enter:
```

sudo cp /cdrom/Setup/Data/base/*.pk4 /usr/local/games/doom3/base/

```
Once the files have been copied, unmount and eject disc one and then insert disc two. After disc two has been mounted, run the above code again. Follow the same instructions for disc three. After all .pk4 files have been copied to your hard drive, you may now play Doom 3. However, you will need the CD key in order to unlock the game. The CD key is found in the jewel case.

---

### Post by AngryKidJoe on 2006-06-08
Thanks, I figured that's what I had to do, but I'm still quite new with Linux and am unfamiliar with the commands. Thanks. *thumbs up*

---

### Post by Sequent on 2006-06-15
Try using

sudo sh ./doom3-linux-1.3.1302.x86.run

(note the period before the forward slash)

---

