---
title: "Is krfb problematic??? How can I setup x11vnc as alternate?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by frikaki on 2005-12-12
I have setup krfb in kubuntu and I think it is a bit buggy....
When I am connecting remotely to my system the cpu runs on full load (100% CPU Usage!!!!) and of course I can`t do anything :( 
I have try krfb in 3 different PC`s running kubuntu (and slackware 10.1 and slamd64) and I`m always getting the same behavior :( 
So obviously this not a distro specific problem but a krfb problem..

I have try to use x11vnc as alternate and it works perfectly (0-5% CPU Usage) but here is another "problem" that I haven`t figure out how to solve it!
If I setup x11vnc I want to set it up in the way krfb works. So I need to make it operate on startup.
How can I do that?


I am using this command to work using x11vnc:

First I am setting a vnc password using the vncpasswd command and then:
> x11vnc -rfbauth $HOME/.vnc/passwd -forever -bg

but I have to enter it everytime I am restarting my system.

Is there a way to make this automatically after restarting or logging out?

---

### Post by CyberAngel on 2005-12-12
Sorry
The problem described above is mine....

I was posting from my friend`s computer and I forgoten to change the account was already logged in (his account).

---

### Post by CyberAngel on 2006-01-03
Finally I found a Solution to this problem!!!!!
I am posting below just if anyone cares ;) 

***That is generic for KDE***
-----------
Finally I Found how to make something startup per user when this user logs into KDE!!!

There is a folder under everyone`s home directory called ".kde/Autostart"
Generally if you type 
```
cd  ~/.kde/Autostart
```
You should be there ;)

In this folder you can make bash scripts or symbolic links that are executed everytime this user logs in his KDE Desktop environment ;) 
--------------------------


***The following is specifically for x11vnc*** :cool: 
--------------------------
First of all you need to apt-get the x11vnc so do:
```
sudo apt-get install x11vnc vncserver
```

Then you need to create the password that you will be using when you are trying to login to your x11vnc server.
```
vncpasswd
```

Then you have to create the startup script and place it under **~/.kde/Autostart/x11vnc**
```
vi ~/.kde/Autostart/x11vnc
```

This file contains the following lines:
```
#! /bin/sh
x11vnc -rfbauth ~/.vnc/passwd -bg -forever &

```

Save the file and exit. Then make the above file executable using the following command:
```
chmod 700 ~/.kde/Autostart/x11vnc
```

And it is ready :D :D 

Now everytime I am logging in KDE x11vnc starts automatically and I have thrown to the garbage krfb that burns my cute CPU with making it working at 100% without reason :p :KS

---

### Post by shizow on 2006-01-17
is it possible to have more than one connection to x11vnc, when i try to connect to our server from two different computers to work in the same session,  that does not work

---

### Post by Divan Santana on 2006-01-18
Cyberangel!!! Thank you!!

This is very much a known bug for a while! It looks as if Ubuntu and/or KDE doesn't seem to ever fix it. The problem has been a while for many versions of Kubuntu! krfb is basically useless because of CPU usage. 

But this easy alternative you have setup is brilliant! Thanks for the post I certainly care!

Btw since I've been struggling for a while looking for VNC like program I am using freenx and it is awesome! Only it doesn't connect to same session like VNC does so is not ideal for support and helping users...

---

