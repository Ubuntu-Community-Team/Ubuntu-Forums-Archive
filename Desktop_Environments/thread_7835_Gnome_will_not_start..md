---
title: "Gnome will not start."
date: 2004-12-11
forum: Desktop Environments
---

### Post by elder68 on 2004-12-11
Ubuntu is set up on an AMD/Duron unit and has been updated. Yesterday I tried to install the Acrobat Reader, from Adobe, with "gunzip" and "tar"  and then used their "install" and it was installed on /usr/local/Acrobat5.

This morning when I booted Ubuntu it brought up the log-in screen, I entered my username and password and the screen blanked to the Ubuntu background color, then it went black and then it brought up the log-in screen again. It seems to be caught in a loop. Acrobat tells you it can be removed by simply removing the directory and I did this by going into the "safe mode" but this did not make any difference. 

As the system boots the Gnome system "GDM" seems to be starting OK. So I went back and booted the kernel in the safe mode, and when it loaded I gave the command: #startx, the screen flickered a bit and then Gnome started OK. But when I restart the unit again, it goes back to the original looping problem I outlined above. 

Any help would be appreciated.

Bill.

---

### Post by taygan on 2004-12-11
make sure the config files in your home directory are owned by you..  I had the same problem when k3b changed .ICEauthority to root ownership..

From the terminal in your home directory (/home/$USER)

to check:  ls -l
to change: sudo chown -R $USER:$USER *.*
the -R should make everything in the directories in your home folder owned by you.

---

### Post by elder68 on 2004-12-12
[QUOTE=taygan]make sure the config files in your home directory are owned by you..  I had the same problem when k3b changed .ICEauthority to root ownership.. From the terminal in your home directory (/home/$USER) to check:  ls -l to change: 
sudo chown -R $USER:$USER *.*
the -R should make everything in the directories in your home folder owned by you.[/QUOTE]

Thank you for this and I wish I could say that it solved the problem. I did as you suggested above and it did not make any difference. I went in as root and checked the permissions on each and every file and directory and they were all set to the me, the $USER, with read, write and execute permissions. 

Any further suggestions would be appreciated. I just upgraded Ubuntu, downloading over 100 Mb of files over a dialup line, and don't want to have to repeat the process by re-installing Ubuntu.

Bill.

---

### Post by taygan on 2004-12-12
I first tried fixing my gnome reboot cycle by removing my gnome and gtk configuration files (some of the hidden .files in your home directory and the root directory)  It removed all my customization and didn't actually help me, but that's what was recommended to me, and I was able to recustomize the system without too much hassle.  It seems that gnome is trying to boot but is hanging in the configuration stage..   

May as well try it, especially if you backup the files :)

---

### Post by elder68 on 2004-12-12
[QUOTE=taygan]I first tried fixing my gnome reboot cycle by removing my gnome and gtk configuration files (some of the hidden .files in your home directory and the root directory)  It removed all my customization and didn't actually help me, but that's what was recommended to me, and I was able to recustomize the system without too much hassle.  It seems that gnome is trying to boot but is hanging in the configuration stage..   
May as well try it, especially if you backup the files :)[/QUOTE]

Well life if full of surprises. I intended to re-install but decided to  look one more time. Looked at the "home" the home folder itself. I was not the owner and made the change, and  after that the unit booted OK.

Thanks for your help,

Bill.

---

### Post by Neobuntu on 2006-05-07
[QUOTE=elder68]Well life if full of surprises. I intended to re-install but decided to  look one more time. Looked at the "home" the home folder itself. I was not the owner and made the change, and  after that the unit booted OK.

Thanks for your help,

Bill.[/QUOTE]

Nope! This did not work for me. I did...

sudo chown -R user.user /home/user 

... "user" being YOUR user name.

All home files are now NOT root owned and still GDM is looping with no Gnome startup. 

I also purged gnome and reinstalled per anouther thread and still with the looping. :(

UPDATE:
It was my old "xorg.conf" Gnome starts as user now, it was X as I went to dapper. See...
[http://www.ubuntuforums.org/showpost.php?p=994465&postcount=7](http://www.ubuntuforums.org/showpost.php?p=994465&postcount=7)

---

