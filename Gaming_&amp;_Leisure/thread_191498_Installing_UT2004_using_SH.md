---
title: "Installing UT2004 using SH"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by drummer4lifex on 2006-06-07
Hello all! This is my first post. After extensive research and trying several distros, I have found myself constantly coming back to Ubuntu. So here I am ready to learn!

For my first problem: I'm installing UT2004 which requires you to browse to the cdrom in the terminal and run the sh linux-installer.sh command. The problem I'm encountering is that it wants to install the game in the /usr directory yet I don't have write/execute permissions. How do you login as root to change these? 

The second issue is that the cdrom won't unmount when it asks for CD2, and when I use the pin to open the drive and put CD2 in, it can't read CD2. I'm guessing because CD1 isn't umounted in the software yet, but I don't know. How do I get past this?

Thanks in advance,

Paul

---

### Post by DoktorSeven on 2006-06-07
From any directory other than the cdrom directory:
**sudo bash /media/cdrom/linux-installer.sh** (or whatever the path to it is).

Using sudo (which asks for your password) will let you install in /usr, and specifying the full path from outside the cdrom directory will allow you to unmount the CD when it asks.

---

### Post by siorai on 2006-06-07
When installing from the CDs, you need to copy the installer to your harddrive first (doesn't matter where) and run it from there.

---

### Post by MetalMusicAddict on 2006-06-07
[QUOTE=siorai]When installing from the CDs, you need to copy the installer to your harddrive first (doesn't matter where) and run it from there.[/QUOTE]
Along with this I install everything to /home/USER/.ut2004. I can actuall just copy that directory to a DVD and copy it back after a OS reinstall. No problems.

---

### Post by chrism66 on 2006-06-08
Ok I have two questions:

1.) UT 2004 will not start after i ran it at the end of the installtion. It just flashes the start window for a mili second and that's it. Any clues????

2.) What is the easistest way to extract the updates? All the files and diretories in my UT 2004 diretory are locked.

I know that this are stupid questions but what do you expect from a 'Newbie'!!!

Well thanks in advance for any help!!!

Regards,
Chris

---

### Post by Harleen on 2006-06-08
[QUOTE=chrism66]1.) UT 2004 will not start after i ran it at the end of the installtion. It just flashes the start window for a mili second and that's it. Any clues????

2.) What is the easistest way to extract the updates? All the files and diretories in my UT 2004 diretory are locked.

I know that this are stupid questions but what do you expect from a 'Newbie'!!!

Well thanks in advance for any help!!!

Regards,
Chris[/QUOTE]

1) You installed with sudo and clicked on the "play now" button at the end of the installation. Now the .ut2004 directory in your home directory belongs to root. You can change the owner of that direcory back with this command:
chown <username> ~/.ut2004 -R
You have to replace <username> with your actual user login, of course.

2) extract the files somewhere and copy the files as root over your installation, which is usually located under /usr/local/games/ut2004
Supposed you have a command shell in the directory, where you extracted the files, you have to type this:
sudo cp * /usr/local/games/ut2004 -R

Edit: Probably an easier method for extracting files (at least I'm doing it that way) is using the midnight commander.
Start it as root using "sudo mc" and then navigate in one pane to /usr/local/games/ut and in the other pane navigate into the compressed file with the updates and simply copy the files.

---

### Post by daz_worldwide on 2006-07-15
cheers for the advice!  It worked no problem

---

