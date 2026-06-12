---
title: "Gnome and Fluxbox"
date: 2008-05-13
forum: Desktop Environments
---

### Post by grjemo on 2008-05-13
I have seen numerous posts regarding running Gnome and Fluxbox together.  They all confuse me.  Is it even possible?  How exactly would I go about doing this?

---

### Post by cylux on 2008-05-13
Hey. Yes you can run Fluxbox within Gnome. 

Carefully follow the steps outlined in the following link, if they don't work or something is unclear, feel free to ask and I'll clarify.

[http://ubuntuforums.org/showthread.php?t=63734](http://ubuntuforums.org/showthread.php?t=63734)

---

### Post by grjemo on 2008-05-14
When I enter:

*sudo /usr/share/xsessions/fluxbox.desktop*

I get:

*sudo: /usr/share/xsessions/fluxbox.desktop: command not found*

---

### Post by rgeddes on 2008-05-14
> **grjemo said:**
> When I enter:

*sudo /usr/share/xsessions/fluxbox.desktop*

I get:

*sudo: /usr/share/xsessions/fluxbox.desktop: command not found*

From corrections to the original guide it should be:

$ sudo gedit /usr/share/xsessions/fluxbox.desktop

---

### Post by grjemo on 2008-05-14
I did my best to follow the directions, but I now have no window manager at all.  Some things it may have been:

When I was supposed to replace exec=fluxbox with exec=startfluxbox, the line was not exactly exec=fluxbox, it had additional stuff at the beginning, and was already set to startfluxbox.

Also, the line 1,RestartCommand=gnome-wm --sm-client-id default1 was actually 0,RestartCommand=gnome-wm --sm-client-id default1.

---

### Post by kerry_s on 2008-05-14
> **cylux said:**
> Hey. Yes you can run Fluxbox within Gnome. 

Carefully follow the steps outlined in the following link, if they don't work or something is unclear, feel free to ask and I'll clarify.

[http://ubuntuforums.org/showthread.php?t=63734](http://ubuntuforums.org/showthread.php?t=63734)

those are some very old instructions.

for fluxbox all you have to do is:
sudo apt-get install fluxbox menu
sudo update-menus
logout
select fluxbox in the session menu and log in.

then just add the gnome stuff you want to use from gnome to ~/.fluxbox/startup

---

### Post by grjemo on 2008-05-15
> **kerry_s said:**
> then just add the gnome stuff you want to use from gnome to ~/.fluxbox/startup

How would I go about this?

---

### Post by kerry_s on 2008-05-15
> **grjemo said:**
> How would I go about this?

example, say you want the gnome panels, you would put:
**gnome-panels &**

in the startup

---

### Post by grjemo on 2008-05-15
I'm just wondering the names of the stuff I can put in. Is there a site with this?

---

### Post by kerry_s on 2008-05-15
> **grjemo said:**
> I'm just wondering the names of the stuff I can put in. Is there a site with this?

i normally look in synaptic, at my installed programs. usually /usr/bin is where the programs go, that will tell the name it runs by. see pic

---

### Post by grjemo on 2008-05-15
It works! I love it!

EDIT: I cant get the notification area working. Put it on the panel, but nothing... is there a package I need to put in the startup file for that?

---

### Post by kerry_s on 2008-05-16
> **grjemo said:**
> It works! I love it!

EDIT: I cant get the notification area working. Put it on the panel, but nothing... is there a package I need to put in the startup file for that?

the notification area, you mean the dock?

i believe you can only have 1, so since your using gnome panels you can disable the fluxbox panel or remove the dock portion from that panel, look in ~/.fluxbox/init i think it is, sorry i'm a little rusty on my fluxbox, i switched to jwm and haven't looked back.

mine->

---

### Post by grjemo on 2008-05-16
No, I mean the notification area in the gnome panels.

---

