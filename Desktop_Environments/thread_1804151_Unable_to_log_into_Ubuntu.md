---
title: "Unable to log into Ubuntu"
date: 2011-07-14
forum: Desktop Environments
---

### Post by Brooksy_FC on 2011-07-14
Hey Guys,

I've just installed Gnome3 onto Ubuntu, as I thought it looked better than the other desktop. After the installation, it told me to restart my system, so I did.

Now I can't seem to log into any sessions. :( In my list I have GNOME, Recovery Console, Ubuntu and User Defined Session. Everytime I try and log into one I get the same message, for example, "Failed to load session "gnome"

Any ideas around this or anyone that has had the same issue have a solution??? :confused:

P.S. I'm kinda new to Ubuntu

---

### Post by enimeizoo on 2011-07-14
Can you post the content of the .desktop files in /usr/share/xsessions ?

---

### Post by Krytarik on 2011-07-14
Please see the start of this how-to:
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

Greetings.

---

### Post by Brooksy_FC on 2011-07-18
Thanks for the link, this should help me a lot...

How can I access the terminal if I can't log in to anything? :neutral:

---

### Post by Krytarik on 2011-07-18
> **Brooksy_FC said:**
> 
How can I access the terminal if I can't log in to anything?
Well, good question, it's apparently not included in those how-to:

When you are at the login screen, just press Ctrl+Alt+F1 to get the console login.

After re/installing the "gnome-session" package or other packages possibly related to GDM, restart the latter, this would also bring you back to the login screen:
```
sudo service gdm restart
```To just switch back to the login screen without restarting GDM, press Ctrl+Alt+F7 or F8.

Hope this how-to and the followed thread helps you, as I'm really not that into Gnome 3 so far. Or maybe another forums member steps in, to give you more Gnome 3 specific support.

---

### Post by Brooksy_FC on 2011-07-19
Thank you very much for your help. I'll give it a try :P

I'm only using Ubuntu to try out some Java for a website I need to edit. I'm all new to this haha. I'll have to check some other forums on that I think.

What are you using as your GDM? I only tried GNOME 3 cause it looked better than the default.

---

### Post by Krytarik on 2011-07-19
> **Brooksy_FC said:**
> 
What are you using as your GDM? I only tried GNOME 3 cause it looked better than the default.
Well, I'm using Gnome in Lucid 10.04, but not with the usual Gnome Panels, instead with AWN.

Btw., GDM is just Gnome Display Manager, it can invoke any other Desktop Environment (DE) as well. Just to make the terminology clear.

---

### Post by Brooksy_FC on 2011-07-19
Ah I see now. I'll look into it. 

Many thanks for your time :)

---

