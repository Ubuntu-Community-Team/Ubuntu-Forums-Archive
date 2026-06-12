---
title: "what are they where do i find list????"
date: 2005-12-23
forum: Desktop Environments
---

### Post by bullfrog on 2005-12-23
**what are the commands to install real player from desktop??? first one i have  run from from termial---"chmoda+xREALPLAYER10GOLD.bin" second--run---:./REALPLAYER10 GOLD.bin ---followinst. to finish installing.      now ineed to know what goes before each.   also where can i find the commands to do everything with.   thanks alot for your help bullfrog:confused: **

---

### Post by NeghVar on 2005-12-23
The real player website has this for install instructions:

Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!


For a basic list of commands you can look at:

[http://www.tuxfiles.org/linuxhelp/linuxcommands.html](http://www.tuxfiles.org/linuxhelp/linuxcommands.html)

hope that helps.

---

### Post by rikai on 2005-12-23
[This link]("https://wiki.ubuntu.com/RealplayerInstallationMethods") should help you out.

---

### Post by KeyboardJockey on 2006-02-18
I've tried the above instructions and this is what I've got.  What have I done wrong - again:( 

marc@ubuntu:~$ chmod a+x RealPlayer10GOLD.bin
marc@ubuntu:~$ sudo chmod a+x RealPlayer10GOLD.bin
Password:
marc@ubuntu:~$ ./RealPlayer10GOLD.bin
Extracting files for RealPlayer installation........................

Welcome to the RealPlayer (10.0.6.776) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...


Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/marc/RealPlayer]:



















You have selected the following RealPlayer configuration:

Destination:            /home/marc/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: f



















Copying RealPlayer files...sh: line 1: /home/marc/RealPlayer/install.log: Permission denied
sh: /home/marc/RealPlayer/install.log: Permission denied
sh: install.log: Permission denied
sh: line 1: /home/marc/RealPlayer/install.log: Permission denied
./postinst/postinst.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied
configuring mozilla...
./postinst/postinst.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied
./postinst/postinst.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied
./postinst/postinst.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied
./postinst/postinst.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied
Configuring realplay script...
cp: cannot create regular file `realplay.bak': Permission denied
/home/marc/RealPlayer/postinst/confscript.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied
/home/marc/RealPlayer/postinst/confscript.sh: line 43: realplay: Permission denied
/home/marc/RealPlayer/postinst/confscript.sh: line 45: /home/marc/RealPlayer/install.log: Permission denied

RealPlayer installation is complete.
Cleaning up installation files...
Done.

---

### Post by KeyboardJockey on 2006-02-18
I've looked into the home folder and found that the RealPlayer folder has a padlock icon on it.  How do I change the status of this file so that I can get rid of it and try to re install RealPlayer?

thanks

---

### Post by cbudden on 2006-02-18
You need to run the installer as sudo so do :

```
 sudo ./RealPlayer10GOLD.bin 
```

---

### Post by KeyboardJockey on 2006-02-18
[QUOTE=cbudden]You need to run the installer as sudo so do :

```
 sudo ./RealPlayer10GOLD.bin 
```[/QUOTE]

Right I've done this and it has re installed Real Player 10 it still plays mp3's ok but is still not picking up online radio.

I really think I need to delete the file in the home folder with the padlock icon on it tht says Real Player but I can't delete it it says that I dn't have enough priviledges!!

I'm trying to get rid of ALL  files and folders tht sayreal player as I've resigned myself to having to go to the Win XP OS to listen to online radio as I'm convinced that this particular audio streaming format that the BBC uses just doesn't work with Ubuntu.  

I'm quite happy with VLC and CDPlayer to play music and video files.

---

### Post by ade234uk on 2006-02-18
Why dont you just install automatix. You can choose to install Realpayer from the menu. It gets all your media players up and running codecs as well.

---

