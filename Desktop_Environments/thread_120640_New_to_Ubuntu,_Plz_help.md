---
title: "New to Ubuntu, Plz help"
date: 2006-01-23
forum: Desktop Environments
---

### Post by Orion2014 on 2006-01-23
Ok, I finally installed Ubuntu 5.10, and i need some help. Here is all i want to accomplish.

Install Wine

Mount my second HD which is NTFS

Install my HP USB printer  (PSC 1210)

Yesterday i installed and was able to get all my updates, and my printer responding, but every time i printed it came out blank. I figured out how to use apt but something went wrong yesterday so i completely reinstalled this morning, as apt wasnt working at all. I want to install wine for some of my older programs, and i really, REALLY need help mounting my second hard drive, since i backed up all my pics and music onto it from windows and now i cant access it at all. when i go to my disks manager, i click enable and it does nothing. 

PLZ HELP!!!!!!!!!!!!!![-o< [-o< [-o<

---

### Post by nominal on 2006-01-23
I can help you get wine, but sorry thats it :) 

This is what you wanna do:

1. [Go Here]("http://ubuntuforums.org/showthread.php?t=66563")
2. D/L Automatix
3. App-->SystemTools-->Automatix
4. Read the notice about Wine.
5. Choose Wine from the menu, and wait for it to d/l and install!

About your hard drive though...you might wanna go to the company site, and see if they have some help for you. Your printer--i can only think about drivers.

---

### Post by carlosqueso on 2006-01-23
Mounting your hard drive shouldn't be a problem.  Go into your /etc/fstab file by typing ```
sudo gedit /etc/fstab 
```.  Post that here, so I don't tell you to do the wrong thing.  As for the printer, try looking in the gnome-cups-manager dialog.  (hit Alt+f2 and type gnome-cups-manager) for your printer.  This website may also be helpful. [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210)

---

### Post by bikeman on 2006-01-23
As for accessing your NTFS drive, start here:
**sudo fdisk -l **(that's the letter l not a number 1) to list your disks, note the location of the NTFS drive for step two:
Assumed that /dev/hda1 is the location of Windows partition (NTFS) Local mount folder: /media/windows (change these to match your system in the commands below)

Type

[B]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/B]

Append the following line at the end of file:

**/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0**

Save the edited file.

Then remount the /etc/fstab file like this (or reboot your PC):
**sudo mount -a**

Now you should have read-access to the NTFS drive.

I can't help you on the other stuff.  Automatix is great, as is the unofficial Ubuntu guide (that's where these instructions came from) at:  [Unoffical Guide]("http://ubuntuguide.squarecows.com/doku.php")

---

