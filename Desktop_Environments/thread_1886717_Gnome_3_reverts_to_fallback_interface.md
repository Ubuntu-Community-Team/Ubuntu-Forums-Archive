---
title: "Gnome 3 reverts to fallback interface"
date: 2011-11-25
forum: Desktop Environments
---

### Post by larikaram on 2011-11-25
Hi guys! 
I've read a lot of the posts on this forum and others on how to install gnome 3 but it seems I keep having the same problem and something is not working right with me! Need a little help here! 

Here is my situation: I'm on Ubuntu 11.10 (with Unity), and everything is working sweet on my workstation with no problem what so ever. I decided to install Gnome 3 and the process seemed to have worked great for the first time and running perfectly! 

When I log out, and log in again, I loose the gnome 3 interface and I'm left with the fallback interface (old gnome style). 

I thought it was because I uninstalled Unity ... reinstalled Unity and Gnome 3 > works the first log in then if i log out switches back to old gnome.

I reinstalled a fresh copy of ubuntu, kept Unity and Installed Gnome 3 same issue! 

I also noticed that I don't have a ~/.themes after I install Gnome...

One last note, I have a Nvidia Quadro FX 4000, but not sure it has to do with my situation. The default drivers works great with it! 

Any help would be appreciated! :confused:

thx 
lari

---

### Post by Frogs Hair on 2011-11-25
You will need to create a .themes and .icons folder in home / hidden folders in  11.10 . Theme installation works differently in 11.10 and the drag & drop option in appearance preferences has been removed . The Gnome Tweak Tool / Advanced Settings is required to change themes .  
    
I don't know why the shell reverts to fall-back upon logout or shut down . When using a manual login , the last session used is what is what appears on the session menu when booting or logging in if everything is working properly .

---

### Post by QDR06VV9 on 2011-11-25
I had the same problem!
Sounds like and I am not a real authority but a hardware or or driver problem!
Ive checked this out and like this system, It will be a unofficial fork of gnome3 remix
over ubuntu with no unity at all! Worth a look to see if you want some more adventure!

Link for Info: [http://www.howtogeek.com/96172/bypass-the-unity-ui-altogether-in-ubuntu-11.10-with-the-gnome-shell-remix/](http://www.howtogeek.com/96172/bypass-the-unity-ui-altogether-in-ubuntu-11.10-with-the-gnome-shell-remix/)

Download link: [http://ubuntu-gs-remix.sourceforge.net/p/download/](http://ubuntu-gs-remix.sourceforge.net/p/download/)
With 32 bit and 64 bit choices

Sorry try frogs Hair suggestion first!

---

### Post by cbowman57 on 2011-11-25
Sometimes deleting ~/.local/share/gnome-shell/application_state clears that up.

---

### Post by larikaram on 2011-11-25
Thx guys for the help! 
I'll try your suggestions this afternoon! 

I have created a .themes but not the .icons ... I thought though that it was looking for those in /usr/share/gnome-shell ... but i'll try it and keep you posted on what happens! 

thx

---

### Post by Frogs Hair on 2011-11-25
If you want to make themes and icons available for all users and appear when root is used place them in file system > usr > share icons or themes .

---

### Post by larikaram on 2011-11-28
Hey guys again! 
sorry I couldn't reply earlier! thx for all the help.. but none worked for me!

don't know if you have any other suggestions ... 
I edited the gnome-fallback.session file in /usr/share/gnome-session/sessions
and replaced the gnome-fallback with gnome-shell and now everytime I log in I get the gnome-shell interface working fine! LOL.... 

I'm still gonna look closely to it and see what's going on with my gnome.... i'll post an update soon... 

thx

---

### Post by cbowman57 on 2011-11-28
Gnome does apply some type of logic when it selects fallback instead of the shell.

I remember in the early days I actually ran across a hack that disabled detection if you knew the vidcard was capable.  Essentially you did the same thing, only easier. :)

---

