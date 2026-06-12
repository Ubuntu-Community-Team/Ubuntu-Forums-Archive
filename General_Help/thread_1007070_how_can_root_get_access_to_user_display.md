---
title: "how can root get access to user display?"
date: 2008-12-10
forum: General Help
---

### Post by jansch75 on 2008-12-10
I have an udev script which starts after I plug my external USB hard drive into the computer. This script will run with root privileges. I have problems to allow this script to pop up some zenity notes on the user screen...

The important lines of the script

```
#!/bin/bash
export DISPLAY=:0.0
su USERNAME -c '/usr/bin/zenity --question --text "Do you want to remove external hard drive?"'
```

On one of my Ubuntu Hardy heron computers this script works well. On the other machine I have to give the root first access to the user display by typing
```
xhost +local:USERNAME
```
into a terminal as normal user with the name USERNAME. 

Otherwise I will get the error "No protocol specified" and "Could not connect to display 0.0".

My questions: Why does it work on one computer without the xhost permission? How can the root automatically get the right to use the display of the user...?

I have googled now one week but so far I could not find any solution which helps me. Is it possible to run xhost +local:USERNAME during boot? Are boot scripts also running under root privileges? Is this a security risk?

Thanks to every experienced bash script writer who could help me here... I started bash programming a few weeks ago and in the moment I am not coming further... So again, REALLY THANKS, if somebody can help here

---

### Post by ket000 on 2008-12-25
I found the following solution to make it work, but i don't know it is the best, but it works for me.

go to terminal 
1. sudo gedit /root/.bashrc and add the following line at the end.
export DISPLAY=:0.0

2. login as root by typing su -
   ln -s /home/<normalusername>/.Xauthority .Xauthority

for e.g. if normal username is ketan then it will be

ln -s /home/ketan/.Xauthority .Xauthority

After that it works fine.

My question is I don't have to do anything in fedora 10 and only ubuntu requires this for granting root user access to user display. There must be a better way of doing this in ubuntu 8.04

---

### Post by MaxIBoy on 2008-12-25
Try modding your script like this:
```
#!/bin/bash
export DISPLAY=:0.0
gksudo USERNAME -c '/usr/bin/zenity --question --text "Do you want to remove external hard drive?"'
```

---

