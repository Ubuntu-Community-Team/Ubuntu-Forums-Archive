---
title: "ieee1394 camcorder"
date: 2006-09-08
forum: Desktop Environments
---

### Post by iammeagain on 2006-09-08
Vino won't allow me to capture off my camcorder. i looked at different things, here is was i have tried so far: 


#i did this to get ieee1394 to maybe work with camcorder

sudo kwrite /etc/init.d/bootmisc.sh

#then added this too it:

# Begin Edit. 20041031 RCB - Added to hopefully get the raw1394 devicenode.
 mknod /dev/raw1394 c 171 0
 chown root:video /dev/raw1394
 chmod 666 /dev/raw1394
 #End Edit
 

# then i 

sudo kwrite /etc/init.d/bootmisc.sh

# and added

raw1394
video1394

 this worked for a lil bit, but if i pressed capture or stop buttons more then once i crashed. The two only worked somewhat together. any other ideas on how to fix it. i already trieed running Kino as root and it wouldn't do anything at all.
#  so i could only press on only once. That doesn work too well...

---

### Post by efreddi on 2006-11-29
This is the way I fixed the problem:

in **/dev** I found a folder called **dv1394**. Inside it there is a file called **0**, so I did

**sudo chmod g+rw /dev/dv1394/0**

then in the properties of Kino, in the tab *IEEE 1394* in the field for the *dv1394 Device* I wrote

**/dev/dv1394/0**

that's all, Kino works perfectly. Probably it was better to try to setup a group for video, but I don't know how to do it.
Ciao


Elia

---

### Post by iammeagain on 2006-12-25
kool thanx for the tip, our video camera is having problems, mainly recording now. lol just my luck. But i can still try and see if it will allow me to capture the video from it.

---

### Post by efreddi on 2007-01-06
Here a better way to fix the problem.
The firewire is owned by root and shared in the group ***disk***. So it's necessary to add your account in this group. You can do in this way. In the terminal type:

**sudo gedit /etc/group**

you will see a list of available groups, then find ***disk***:

[B]...
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
...[/B]

add your username at the end of the line of disk:

**disk:x:6:*your_name***

Save and reboot. In this way now you are member of the group ***disk***, so you have the rights to access the firewire. That's all, on my pc it woks perfectly.
Best regards


Elia

---

