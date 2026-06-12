---
title: "Guide to help install Unreal Tournament 2003?"
date: 2007-03-12
forum: Gaming &amp; Leisure
---

### Post by bash on 2007-03-12
I read that it is possible to install UT 2003 in Linux and play it there nativly. Now I tried googlin it but so far I only found installation tutorials for UT 2004. Are there any for UT 2003?

---

### Post by ruibuntu on 2007-03-27
Download the loki instaler from 
[http://www.liflg.org/?catid=6&gameid=70](http://www.liflg.org/?catid=6&gameid=70)

and run like superuser. then it's like just linux.:lolflag:

---

### Post by jollyollyman on 2007-10-10
Ok, on the third disk of UT2003 a shell script was included to set the game up.  Go to console and run the script a superuser.  It'll run just like a windows app after that.  A big thank you to Epic for not keeping me away from the good games.

---

### Post by scod on 2007-11-18
i hace 1 problem,...
when i run the installation script(as root) and when I enter the cd key, i got an error,..

[: 54:==:  unexpected operator
[: 54:==:  unexpected operator
Your cd KEYS don't match, please try again

and i got stucked there!

im guessing some syntax problem with the script xD  anyway, any help?

:(

---

### Post by vidarjb on 2007-12-20
The problem is that the install script for ut2003, is written in bash. sh on ubuntu systems uses dash.

In order to install ut2003, you have to make the system use bash instead of dash.

To do this, do the following:

1. Open a terminal, and navigate to /bin
2. Move the existing sh link to backup: sudo mv sh sh_bak
3. Create a symlink from bash to sh: sudo ln -s bash sh
4. Run the ut2003 installer: PATH_TO_CDROM/linux_installer.sh f.ex /media/cdrom/linux_installer.sh
5. Follow the instructions of the installer
6. When the installation is done, remove the symlink to bash: sudo rm sh
7. And restore the symlink to dash: sudo mv sh_bak sh

The Ubuntu team has replaced bash with dash for several reasons, and it is NOT recommended to replace bash with dash permanently!!

Hope this is useful!

---

### Post by Shinbu-Otaku on 2007-12-21
> **ruibuntu said:**
> Download the loki instaler from 
[http://www.liflg.org/?catid=6&gameid=70](http://www.liflg.org/?catid=6&gameid=70)

and run like superuser. then it's like just linux.:lolflag:

thats really cool, im gonna have to try that when i get home, currently running it under wine and have loads of video problems when i close it :confused: this mite just solve my problem though.

---

### Post by vidarjb on 2007-12-22
> Download the loki instaler from
[http://www.liflg.org/?catid=6&gameid=70](http://www.liflg.org/?catid=6&gameid=70)

As far as I can tell, this is only an update, that can be applied to an installation of Unreal Tournament 2003.

BTW if UT2003 is installed with the installer script on cd 3, there is a problem with the version of libSDL. Due to this, the game runs very slowly.

To make the game use the correct version of libSDL, do the following:

1. If nessecary, install libsdl1.2debian-alsa.
2. Open a terminal and navigate to /usr/local/games/ut2003/System
3. Backup the original  libSDL-1.2.so.0:  sudo mv libSDL-1.2.so.0 libSDL-1.2.so.0_orig
4. Link to the systems library: sudo ln -s /usr/lib/libSDL-1.2.so.0 /usr/local/games/ut2003/System
5. Play the game!

---

### Post by loudnlownoma on 2007-12-23
> **vidarjb said:**
> The problem is that the install script for ut2003, is written in bash. sh on ubuntu systems uses dash.

In order to install ut2003, you have to make the system use bash instead of dash.

To do this, do the following:

1. Open a terminal, and navigate to /bin
2. Move the existing sh link to backup: sudo mv sh sh_bak
3. Create a symlink from bash to sh: sudo ln -s bash sh
4. Run the ut2003 installer: PATH_TO_CDROM/linux_installer.sh f.ex /media/cdrom/linux_installer.sh
5. Follow the instructions of the installer
6. When the installation is done, remove the symlink to bash: sudo rm sh
7. And restore the symlink to dash: sudo mv sh_bak sh

The Ubuntu team has replaced bash with dash for several reasons, and it is NOT recommended to replace bash with dash permanently!!

Hope this is useful!

Worked like a charm!  Thanks!

For some reason, the game ran perfectly on the video side, but the audio was real choppy.  Digging through the readme in the install directory showed an echo command to adjust the sound to use their included sound package or something, and that cleared it up.  Game runs 100% now!  Very nice to not have to run Wine for such a great game!

---

