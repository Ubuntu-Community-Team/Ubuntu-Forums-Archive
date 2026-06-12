---
title: "quake 3 config write permission problem"
date: 2006-05-05
forum: Gaming &amp; Leisure
---

### Post by truthseek on 2006-05-05
hi@ll

the situation:
/home/myuser/quake3/
chown -R myuser:myuser quake3/
chmod -R +rwx quake3/

if I don't "sudo quake3" it can't write the configs.
any hints on what kind of permissions/general settings whousl I use to get it launched properly?

bye@ll

EDIT:
solved:
sudo chown -R myuser:mygourp ~/.q3a/
sudo chmod -R 777 ~/.q3a/

damned hidden directory :-)

---

### Post by minisori on 2006-05-05
sudo chown -R myuser:myuser .q3a

EDIT:

OOPS didnt see you solved it :P

---

### Post by R3linquish3r on 2006-05-07
You actually need to run quake3 as sudo anyway cause when PB updates it tends to *Lock* the folder :/

---

### Post by minisori on 2006-05-07
[QUOTE=R3linquish3r]You actually need to run quake3 as sudo anyway cause when PB updates it tends to *Lock* the folder :/[/QUOTE]

I never ran any game as sudo and i didnt have any problem with pb :confused:

---

### Post by R3linquish3r on 2006-05-07
K. You probably dont use the pbsetup program from evenbalance to update never mind then.

---

### Post by Smokemare on 2006-05-20
the only way i had it working right is to get where you can set the home folder permissions to allow all :)

---

### Post by Perfect Storm on 2006-05-20
Well, it's properly because people hits launch/run <insert game name here> after they installed the game with sudo. It's a no no to do so.
When installed, exit the installer then run the game.

---

