---
title: "system monitor"
date: 2014-05-31
forum: Desktop Environments
---

### Post by beelzebufo on 2014-05-31
I made a similar thread, but I think this one qualifies as a different subject.  I am trying to install a top bar system monitor like I have always had, none of the extensions.gnome.org ones work, I found this, but I can't get it to install properly, I am getting the usual ./configure "inexplicable error" make "no makefile" crap that I always get when trying to install from the damned index repo things, anyway, please help me to get this installed.  [http://ftp.gnome.org/pub/gnome/sources/gnome-system-monitor/3.1/](http://ftp.gnome.org/pub/gnome/sources/gnome-system-monitor/3.1/)  either I have had a stroke in which I lost all intelligence or all repos in which you have to install from a tar are broken, I follow all the directions and they still fail, I have tried everything and a considerable amount of my property has been destroyed due to temper tantrums.  Please help, I can't function without knowing my cpu usage, ram usage, and net speed. 

Thanks in advance
beelzebufo

---

### Post by deadflowr on 2014-05-31
Moved to Desktop Environments


Which gnome-shell version?
Might be helpful.
Stuff that works in one might break in the next, but be fixed in the one after that.
Such is the life of a moving target.

---

### Post by beelzebufo on 2014-05-31
gnome shell version 3.1 I believe, it's the fully supported final version.  I can't figure this out, I have had that panel applet for years, been using gnome for all of them, never ever had a problem

thanks
beelzebufo

---

### Post by deadflowr on 2014-05-31
I probably should said post the output of this
```
gnome-shell --version
```
I don't think gnome-shell 3.1 has been supported on any version for a while.
12.04 uses 3.4, so...
If your on 14.04 then stock is 3.10, if that helps.
(not like it will help, but, hey)

---

### Post by beelzebufo on 2014-06-01
```
wreckingball@wreckingball-PC:~$ gnome-shell --versionGNOME Shell 3.10.4

```

---

### Post by deadflowr on 2014-06-01
Yeah, seems typical of extensions that some end up broken here and there.

I don't know how married you are to having a panel app for this, but if you need something, perhaps conky will work.
Here's some more on that [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

---

### Post by beelzebufo on 2014-06-01
thank you man, but I am very familiar with conky, but I don't want to have to exit to my desktop every time I want to look at something.  has to be the panel applet :(  There HAS to be a way to do this that I am just not seeing

---

### Post by Frogs Hair on 2014-06-01
The system monitor extension(Gnome Shell) 3.10 appearers in the bottom notification area and only reports memory and cpu activity. In order to view it I have  to move the cursor to the bottom of the screen. To enable after activated in the Tweak Tool I used Alt +F2 and restarted the shell with the following. ```
r 
```  This is a default extension included with the repository extensions package , but you could check the extensions page for others that appear in the top panel. 

[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by beelzebufo on 2014-06-01
the one on the extensions.gnome.org doesn't work for me, I even went and tried to manually install, in the comments of that one, there is a suggestion for another one, which I checked out, tried to install manually, but ended up with the standard errors that I get EVERY TIME when I try to install from source.

this has been an extension that I have used ever since I started using linux, this is the first time I have had this hard of a time installing it.  It's always a bit of a pain, but not like this, maybe someone could help me install from these source pages?...

[https://extensions.gnome.org/extension/120/system-monitor/](https://extensions.gnome.org/extension/120/system-monitor/)

[https://extensions.gnome.org/extension/9/systemmonitor/](https://extensions.gnome.org/extension/9/systemmonitor/)


they both have links to the git hub source.  maybe I have to do something else?  I download them, unpack, go to the folder in terminal, do a ./configure, then make and make fails, like every other time, why can't we just make source that works?

---

### Post by Frogs Hair on 2014-06-02
I have installed extensions in previous versions of the shell by extracting the packages and placing the folders in the following location. Opening Nautilus as root is required to add or remove items. ```
gksudo nautilus
```computer/usr/share/gnome-shell/extensions

Edit : I have not built extensions from source .

---

