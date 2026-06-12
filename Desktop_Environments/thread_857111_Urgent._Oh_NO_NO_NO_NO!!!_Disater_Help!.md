---
title: "Urgent. Oh NO NO NO NO!!! Disater? Help!"
date: 2008-07-12
forum: Desktop Environments
---

### Post by nunrgguy on 2008-07-12
In the early hours of this morning I was working on my var/lib/mythtv folder - preparing for backups. I've been having some issues lately and needed to change file permissions which I do with Nautilus. Running Nautilus as sudo I scrolled down (so I thought) to permissions at the bottom of the menu and clicked. Only I missed and got the menu item above!!! Move to trash!!! Arghhh.
My whole life was in that folder - over 500Gigs worth of movies, music, my sound sample and synth patch collection (the box doubles as a file server for a recording studio). Nautilus appeared to lock up and wouldn't allow me to cancel. Hours and hours later the folder is gone. I cannot open the trash folder - the drive just churns away for hours and then terminal kills Nautilus. If I right click on Trash 'Empty Trash' is greyed out implying it's empty. If I go to the folder /root/.Trash where I would expect my files to be it contains nothing apart from the 3 files that were already in there and can be seen in Thunar's wastebasket.
BTW the install is Mythbuntu but I've posted here as I'm using the Nautilus GUI and more people are likely to see this post here and have a possible solution.

Where on earth have my files gone? How do I get them back?

Thankyou 
Thankyou
Thankyou

---

### Post by bryncoles on 2008-07-12
if you deleted the file in sudo nautilus, then the deleted files might be in the sudo trash. 

use gksudo nautilis to open a root folder browser (i dont know why, but gksudo is advised when using graphical applications as root.)

try and navigate to 

```
/home/YOURUSERNAME/.local/share/Trash/files
```

where YOURUSERNAME is, well, your user name.

see if the folder is there, and drag it to your desktop if it is. 

if its not there, try getting a second hard drive (at least as big as the one you're using now) and use in testdisk (its in the repos) to recover your files. 

see [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

for more information. 

and for future reference, it is safer to change permissions of folders using this command in the terminal:

```
chmod u+rw -R 'FILEPATHTOFOLDER'
```

chmod changes the permissions. u specifies this as for the user - you. +rw gives you read and write permissions and -R makes it recursive - so it applies it to everything within the folder too. filepath to folder is self explanatory. 

the best way (i think) to use this command is to type 'chmod u+rw -R ' (without the inverted commas) and then drag and drop the folder you are interested in into the terminal. that'll auto complete the file path and you wont risk accidentally deleting important folders. 

i hope you can find your files...

*edit*

if the folder was too big for the recycle bin then you might have permanently deleted it, in which case testdisc is your only chance, and you should stop using the computer immediately, or you wont be able to recover anything! reboot using the live cd - that way nothing will get written to your drive. also consider perhaps paying a professional to do the file recovery, as it'll be safer for your data to get someone who knows exactly what they're doing!

---

### Post by nunrgguy on 2008-07-12
Thanks, I'll give that a try - I can't immediately as the machine is locked up again trying to access the trash via the gui.
I do know about chmod but as I was alrady in nautilus I was being lazy...I should have changed it to 775 in the terminal.
I have heard about the gksudo thing - it's something to do with wrong permissions being assigned I think.
I wouldn't be able to find a harddrive as the one I'm using as it's a 2TB LVM  - is testdisk like a file recovery application working on the whole drive or could it be done on a folder basis to another folder on the same drive?

Thanks

---

### Post by bryncoles on 2008-07-12
ive only used testdisk on a flash drive to be honest, so ive never really thought about that question. it comes in two forms though - testdisk is a whole drive recovery program and photorec is a file recovery program. you should still install testdisk, as that is what contains both programs. if you try using photorec you might find it will just recover (or attempt to recover) the file you want. 

and you will still need a separate drive (or separate partition...) at least as big as the folder you are trying to recover, otherwise theres a chance that recovered filed will be saved over files waiting to be recovered, if you see what i mean.

but im afraid ive exhausted my knowledge now! so lets hope someone more knowledgeable than me comes along and weighs in with their thoughts!

---

### Post by rogier.de.groot on 2008-07-12
Personally, I'd open up a terminal (command line window) and use commands like "du" to figure out where all the data went. You can use, for instance:
cd /
du -sh *
You may need to add "sudo " in front of "du -sh *" sometimes; anyway, du will give you a list of all directories, and how much data is in them. Look for the one with 500GB ;)
Then cd into that directory and try du again, listing all the subdirectories again. Repeat until files found. And then just use mv (move) to move them back where they should be.
Anyway, that's what I'd do, but I'm command line happy;)

Good luck!

---

### Post by nunrgguy on 2008-07-12
All suggestions very greatfully received - keep them coming. Not able to try any yet as maching still locked up but as soon as it's available I'll be in there..I just pray it's not done the Windows style thing where if the maount of data is larger than the size set for the trash it jsut immediately deletes the lot.

---

### Post by coffeecat on 2008-07-12
Two ideas. It seems the machine locks up when the GUI tries to cope with whatever has happened. So, either:

Reboot. At the GDM login screen, don't login but do Ctrl-Alt-F1 to get a virtual terminal and login there. Then navigate to /home/YOURUSERNAME/.local/share/Trash/files as an earlier poster suggested and have a look around and/or do the other things suggested from a terminal.

OR

Boot up from a live CD and mount your / partition. You could try navigating around with Nautilus to see what is in /home/YOURUSERNAME/.local/share/Trash/files on the HD but the same lockup might happen. If so you could open a gnome-terminal and do your investigative work in that.

Good luck.

---

### Post by upchucky on 2008-07-12
google for backtrack and carver they are police forensic tools used to recover evidence on computers.

two others are foremost and scalpel.

some are opensource some are not, can't remember which.

---

### Post by jobo1313 on 2008-07-12
Im not sure but i think ubuntu has a temporary log of everything you do, like windows. You really should go to a professional who knowslinux inside and out. I suggest navy system engineer. My brother in law is one and he fixed my problems with vista and linux.

---

### Post by nunrgguy on 2008-07-12
Phew - found it. 
DU wasn't any use in the end  - threw some erros up so don't know I've got a damaged file system or it's jsut because of the lvm.
du: cannot access `proc/9789/task/9789/fd/3': No such file or directory
du: cannot access `proc/9789/task/9789/fdinfo/3': No such file or directory
du: cannot access `proc/9789/fd/3': No such file or directory
du: cannot access `proc/9789/fdinfo/3': No such file or directory

9789 doesn't exist on the drive but I imagine it's on the file allocatino table for some reason.

The files were located, in the end in var/lib/.Trash-0 - var/lib being the mount point for the lvm. I found them by generally poking about. It's only going to take approx 17 hours to copy the files back according to Ubuntu but at least I've got them back.

---

