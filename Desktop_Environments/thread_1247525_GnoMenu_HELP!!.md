---
title: "GnoMenu HELP!!"
date: 2009-08-23
forum: Desktop Environments
---

### Post by FireStorm102389 on 2009-08-23
ok...well, ive read many different things on this topic and i have mine installed...well, i can't change themes or ANYTHING...supposedly ur supposed to be able to right click the icon and click prefferences...wel, mine doesn't have a prefference option, can any1 help and tell me y?

---

### Post by FireStorm102389 on 2009-08-23
can any1 please help? to my knowledge i installed it correctly but it just doesn't give me the option for prefferences so i can't change the theme and how it looks :/

some1 PLEASE help me!!

---

### Post by ccnjim on 2009-08-23
Can you open your GnoMenu and change your theme from there?
If I click the arrow button to the right of shut down/lock buttons a menu opens in the left pane with GnoMenu settings utility.

---

### Post by FireStorm102389 on 2009-08-23
I don't have that option...and when i open the gnomenu it gives me all the stuff but idk where to change the themes?, i don't have an arrow thing by my stuff that lets me shut down the comp and what not

---

### Post by FireStorm102389 on 2009-08-24
ok, well, i uninstalled the gnomenu thing and idk...the menu that i thought was gnomenu didn't dissapear...the menu im using is named "The main gnome menu" and i installed the GnoMenu and i guess idk, cuz I can't find it anywhere...unless its the one i said ive been using...this is what I typed in and what i got back as far as the installation goes:

> david@david-desktop:~$ cd ~/david/Extract/gnomenu
bash: cd: /home/david/david/Extract/gnomenu: No such file or directory
david@david-desktop:~$ cd ~/Extract/gnomenu
david@david-desktop:~/Extract/gnomenu$ sudo make install
[sudo] password for david: 
install -d /etc/gnomenu /usr/bin/ /usr/lib \
	/usr/share /usr/lib/bonobo/servers
install src/bin/GnoMenu.py /usr/bin/
cp -r src/lib/gnomenu /usr/lib
cp -r src/share/gnomenu /usr/share
install src/lib/bonobo/GNOME_GnoMenu.server /usr/lib/bonobo/servers
Makefile: GnoMenu installed.
david@david-desktop:~/Extract/gnomenu$ 


After that there is no other menu listed in the "+add to panel" window...just isn't there...the gnome main menu is the only one apart from the standard menu that is given when u install ubuntu

---

### Post by ccnjim on 2009-08-24
This is what I used to install GnoMenu....................................

> How to install GnoMenu & Theme
 
 by openxs on: Jul 12 2009      
openxs    openxs
-
    
Chris Baker
United Kingdom
Installation on Ubuntu:

Save the GnoMenu file to your desktop (Gnomenu)

[http://launchpad.net/gnomenu/trunk/1.9-final/+download/gnomenu-1.9.9.tar.gz](http://launchpad.net/gnomenu/trunk/1.9-final/+download/gnomenu-1.9.9.tar.gz)

Once it's downloaded, right-click the file and choose 'Extract Here'.

Next you need to make sure the correct dependencies are all installed,
 so open a terminal (Applications >> Accessories >> Terminal) and type in :

```
sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet
```Next, in the terminal you need to change in to the directory you extracted earlier. Type in:

```
cd ~/Desktop/gnomenu
```now type:

```
make install
```This will install GnoMenu, it comes with some themes installed by default.
 Once this is done, you'll be able to right-click on your panel and select 'Add to panel'. 
Select GnoMenu from the list, it'll add an icon to the panel,
 right-click the icon and choose 'Preferences'. From there you'll be able to install 
the menu themes you've downloaded
 and download others from the Internet.

---

### Post by FireStorm102389 on 2009-08-24
ok everyone, thank you for all your help, but i know what i did wrong now...i dind't activate nor did i have all the Compiz files on my computer...so i guess to all the other users out there that want your desktop to look awesome, just make sure you go into your synaptic package manager and install all the Gnome interface compiz packages cuz it gave me a lotta cool options (i ignored the KDE ones) and then just install them and run compiz, its in your menu...then from there u can right click the icon and mess with settings and what not, THEN is when you can go ahead and install the GnoMenu...my entire desktop looks awesome

btw, Kudoes to the black-red theme, looks sweet as hell :D

---

