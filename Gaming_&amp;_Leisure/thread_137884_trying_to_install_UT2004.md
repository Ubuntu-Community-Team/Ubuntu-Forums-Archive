---
title: "trying to install UT2004"
date: 2006-02-28
forum: Gaming &amp; Leisure
---

### Post by sirtigger on 2006-02-28
Need Help installing UT2004 DVD Edition under breezy

---

### Post by MacV on 2006-02-28
Just pop in the dvd and use the linux script on the disk. I believe it;s called linux_install.sh or something like that. It will end in sh. Open terminal, cd to the disk and type "sh 'name of install.sh'" and the installer should take care of it;s self. I've done it on my machine and it isn't hard.

---

### Post by siorai on 2006-03-01
Copy the installer to your harddrive first, doesn't matter where and run it from there.

---

### Post by sirtigger on 2006-03-01
kool thanks i'll try that tonight

---

### Post by steve.horsley on 2006-03-02
I did it 2 days ago. 

1) copy the installer (linux_install.sh)from disk 1 to you home directory

2) Run the installer as root:
sudo ./linux_install.sh

3) follow the instructions from the installer. The default install location is /usr/local/games/ut2004.  DO make sure that the next cd is mounted before pressing YES. And bear in mind that for some reason, the default response when it asks to change the CD is NO. You have to use the left arrow first.

4) I chose not to let the installer create a logical link because it didn't say where it would out it. So after the installer had finished, I did:
> cd /usr/local/bin
ln -s /usr/local/games/ut2004/ut2004 ut2004
I think I have the launcher executable path right there (from memory).

5) play the game. 
$ ut2004
You don't have to run it as root. You may have to edit the keyboard input a bit - my jump key (Ctrl) didn't work straight off.

It stores settings in ~/.ut2004, so you can reset the settings by deleting that folder (like I had to after I accidentally mapped Esc to Jump, and found I couldn't quit the game - had to press the reset button). Every user has their own settings if course, so unlike on windows, my son can't mess my game up for me.

---

### Post by sirtigger on 2006-03-02
hey thanks for the instructions.  I appreciate it alot.

---

### Post by beast2k on 2006-03-03
Sorry for bringing up an allready dead thread but why is it that I have to copy the installer from the CD? I somehow recall Mandrake about version 8 or so had a problem where you coulden't install anything that was on more than one cd we had to disable automount in fstab is this the same problem? I notice that a few other games, all on more than a single CD, did the same if I dont copy the installer from the cd. Is it because when you go to change the cd the cd will be bussy because of the system using the installer? again sorry for bringing this thread up again but I'm trying to understand the underlying reasons for some of these methods, thanks for any input.:confused:

---

### Post by polpak on 2006-03-03
I'm pretty sure that you don't have to copy the file off the CD.

You can probably just cd to the directory the cd is mounted on and do

sudo sh ./name_of_installer.sh

The only reason for copying it to a local directory would be to set the executable flag on the file since files on a CD don't have it by default. But with the command above you don't need the executable flag set. You'd only need it if you wanted to execute the file directly rather than passing it as an arg to sh

e.g.

sudo ./name_of_installer.sh

wouldn't work if the file was on a CD.

---

### Post by beast2k on 2006-03-03
Thanks for replying so quick, okay I think I understand that but why woulden't it be executable after all it is an executable file isn't it? I am using my years as a windows user for referance so with that in mind is it like a read only file on a cd? I don't understand why it woulden't be executable, seeing how thats exactilly what people do with the file. Also how does the file know where the cdrom is? the file is made with the root of the cd as root and so if you take the file off the cd doesn't that take the file out of it's proper context and so the command to execute the file shoulden't work by my logic. Perhaps my logic is the problem lol, thanks for your patience I'm still trying to wrap my mind around some of these concepts in windows this sort of thing is never an issue. Another interesting note like i mentioned in my last post it seems like a similar problem that mandrake had a few versions ago and just tonight crossover office pro5 gave me the same error that I used to get in mandrake when they had the problem something about a problem with supermount, sorry I can't be more specific on the error. Thanks again.  :confused:

---

### Post by BathroomNinja on 2006-03-03
It may very well be, but I tend to backup all of my Games / media before I run them.  I made an ISO of the dvd, mounted the iso, then ran everything from there and it ran great.  The updates where a bit tricky however.  I had to copy the files over by hand (drag and drop) but it all works.  At my last netfest (lan fest, whatever) I was the only linux player and everything played great!

---

### Post by handy on 2006-03-04
I copied the installer onto the desktop, & I don't believe that I had to run as root!?

---

### Post by polpak on 2006-03-04
[QUOTE=handy]I copied the installer onto the desktop, & I don't believe that I had to run as root!?[/QUOTE]

It depends on where you install it to. If you want to install it to somewhere other than your home directory, you have to run the installer as root. The normal game you can just run as your user however.

---

### Post by handy on 2006-03-04
[QUOTE=polpak]It depends on where you install it to. If you want to install it to somewhere other than your home directory, you have to run the installer as root. The normal game you can just run as your user however.[/QUOTE]

Yep, that explains it, thanks...:)

---

