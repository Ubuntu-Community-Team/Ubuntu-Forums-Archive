---
title: "How to install Unreal Tournament 2004"
date: 2009-05-24
forum: General Help
---

### Post by mgtech on 2009-05-24
When I open the UT 2004 DVD and run the .sh file I always get to the point where I am choosing the installation location, and no matter where I go I don't have write privileges. I have administration, privileges, but am not the root. Is there not a way to use synaptic to install the program, b/c it allows me to enter my password, then install programs. The terminal doesn't even ask for a password when trying to install the program.

---

### Post by retiredtechie on 2009-05-24
The answer is here [http://gwos.org/doku.php](http://gwos.org/doku.php)

Make sure you follow the procedure Exactly. Worked for me but what a pain going through all those CDs

---

### Post by Technophobia on 2009-05-24
Hit Alt + F2 to get the run Application window and enter

"gksudo /media/cdrom0/linux-installer.sh"

Wait a little bit for the installer to open up and follow the steps.



After that you might want to patch the game. Download that patch from here

[http://files.filefront.com/UT2004+Linux+v33692+Patch/;4495557;/fileinfo.html](http://files.filefront.com/UT2004+Linux+v33692+Patch/;4495557;/fileinfo.html)

Once the download is complete you must extract it to your desktop temporarily.

Hit Alt + F2 once again and type

"gksudo cp /home/`whoami`/Desktop/UT2004-Patch/* /usr/local/games/ut2004"

Last step if you decided to patch is to insall libstdc++5 from apt-get.

"sudo apt-get install libstdc++5" from a terminal. I'm not sure if the Run Application window will run the command correctly.

"gksudo apt-get install libstdc++5"



Good luck

---

### Post by mgtech on 2009-05-24
So far the installation is working, but its kind of a slow process. It just finished.

---

### Post by Drakkor on 2009-09-23
Installed game,but can't patch, if I try it says I don't have proper permissions ! TIA

---

### Post by retiredtechie on 2009-09-26
> **Drakkor said:**
> Installed game,but can't patch, if I try it says I don't have proper permissions ! TIA

As the instructions mentioned, do NOT run the program from the install script because it will not set the permissions properly. That happened to me the first time I did it :-(

---

### Post by Drakkor on 2009-09-26
tHX,retiredtechie, now how can I uninstall,and reinstall ut2004 ?

---

### Post by The Cog on 2009-09-26
Uninstalling it consists of releting the directory containing the program, and deleting the launcher script placed in /usr/bin. If you intend to reinstall it, it's not worth removing the launcher because the reinstall will replace it amyway.

---

### Post by Drakkor on 2009-09-26
Seems I don't have permissions to remove it either,jeez
guess I have to be root

---

### Post by The Cog on 2009-09-26
If you installed it outside your home directory then yes you need to be root:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

