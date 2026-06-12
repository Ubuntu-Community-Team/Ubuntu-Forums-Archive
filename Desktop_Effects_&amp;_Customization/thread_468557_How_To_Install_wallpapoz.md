---
title: "How To Install wallpapoz"
date: 2007-06-09
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2007-06-09
First Of all Wallpapoz is a 3rd party software that allows you to have multiple desktop wallpapers on different workspaces.  I believe this software is still in development and its not perfect however it does work. 


first of all you will need the package "python-imaging" soo open up synaptic package manager and search for "python-imaging" and install it

Now to install run the following commands in a terminal

wget [http://wallpapoz.akbarhome.com/files/wallpapoz-0.4.1.tar.bz2](http://wallpapoz.akbarhome.com/files/wallpapoz-0.4.1.tar.bz2)

tar -jxvf wallpapoz-0.4.1.tar.bz2

cd wallpapoz-0.4.1

sudo python setup.py install

and if done correctly it should work...let me know if you have questions on how to do this

---

### Post by verucabong on 2007-06-12
> **kdarkentity said:**
> 
and if done correctly it should work...let me know if you have questions on how to do this

Works great!!!

vb

---

### Post by kdarkentity on 2007-06-12
lol enjoy!!

---

### Post by santarulz on 2007-07-06
I don't understnad how it works. I installed it and I'm the GUI. I rename the wallpapers 1,2,3,4 to the path of the image I want to use, save and restart the Daemon but nothing happens. What am I doing wrong?

---

### Post by kdarkentity on 2007-07-08
Well after you start-up wallpapoz and you hit restart to activate the daemon did you change to another workspace to see if it works? also did you actually change the wallpapers that are set to be shown on each desktop?

---

### Post by sakul07 on 2007-08-15
it works.... but...  it takes like 3 secs to work... is not that on the fly... and it doesn't change when i spin my 3d cube....

---

### Post by kdarkentity on 2007-08-15
yea it does kinda suck that it doesent adjust instantly.. i think you can play with the settings for that tho... did u actually set the other sides of wallpapoz to have different backgrounds?

---

### Post by sakul07 on 2007-08-16
yeah.. i did it... and got tired... and then i uninstalled...hehe... i rather wait until some beryl-gnome patch came out...

---

### Post by kdarkentity on 2007-08-16
whatever floats your boat man lol

---

### Post by leap on 2007-09-16
thanks works good installed on 32 bit and 64 bit with no problems

---

### Post by BuntuFreak on 2007-12-24
I could use some help with Wallpapoz. 

First, after I installed and logged out / rebooted and logged back in, I see the "python" process for wallpapoz running. However, sometimes I have to go and "Restart" the daemon, at other times not, after I log on. Wierd.

Bigger problem, I created a guest user on my machine. Not only does Wallpapoz not run automatically for that user, it gives me some "c"/"c++" errors when I try typing "wallpapoz" in a Terminal window. Given that wallpapoz is starting in my user account automatically without having any entry in my "Session", I was thinking it will start for all users on the box. Not to say, I cannot get past this problem. But why doen't wallpapoz work at all when I log in as different user?

Thanks in advance.

---

### Post by rustix on 2008-07-13
awesome! thankss :)

---

