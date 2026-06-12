---
title: "Does xubuntu require gksudo?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by eeried on 2006-09-27
Hello,

I've been using ubuntu since Hoary but I've just found out about gksudo in the Ubuntu Wiki :-? 

Is it necessary or okay in Xubuntu?

Do you need to type Alt + F2 before typing gksudo? What do these keys do?

Cheers,

---

### Post by encompass on 2006-09-27
You don't have to... if you run everything the administers the system in console... basically it is the same thing as sudo but graphical... I use it with windowmaker in xubuntu.
But no it is not REALLY required.  If you like using the mouse and the menus alot then you go right ahead.
Good question...

---

### Post by encompass on 2006-09-27
and about your alt F2 doesn't that open a run dialog?

---

### Post by ayoli on 2006-09-27
> **eeried said:**
> Hello,

I've been using ubuntu since Hoary but I've just found out about gksudo in the Ubuntu Wiki :-? 

Is it necessary or okay in Xubuntu?

Do you need to type Alt + F2 before typing gksudo? What do these keys do?

Cheers,

ALT + F2 opens a run dialog in gnome, maybe it does nothing in xubuntu.
gksudo is a gtk frontend to sudo, it is neccessary to launch admin applications from menu/launchers otherwise you will have to launch these application from command line with sudo to see password prompt.

---

### Post by orb9220 on 2006-09-27
Just gksudo from a terminal instead.

---

### Post by eeried on 2006-10-06
Many thanks for your replies.

My question can't have been very clear though. reading the doc (Ubuntu Wiki) I was under the impression you need to type ```
gksudo gedit
``` when you want to launch gedit as sudo from the terminal. The doc seems to warn you against typing ```
sudo gedit
``` (graphical app) while ```
sudo apt-get update
``` is fine (non graphical app).

Using Ubuntu Breezy before I switched to Xubuntu Dapper I never ever used gksudo because I didn't even know there was such a thing  :-# 

Of course, I understand you don't have to use the terminal but I enjoy using the terminal -- on my oldish computer it does things quicker.

Can you/ Should you/ type ```
gksudo mousepad
``` or can you type ```
sudo mousepad
``` in Xubuntu (with Xfce)? Isn't gksudo a Gnome thing?

cheers,

---

### Post by az on 2006-10-06
gksudo is a GTK thing.  Gnome and XFCE both use GTK.

Using gksudo or sudo is the same thing.  The only difference is that you type in your password into a dialogue box using gksudo.  It is useful for making application launchers that you use instead of having to open a terminal.

Otherwise, from the command line, using sudo would just be more straightforward.

---

### Post by eeried on 2006-10-09
Hello,

Many thanks for your anwser azz :) 

This is what the Ubuntu wiki says in "Root/Sudo" [https://help.ubuntu.com/community/RootSudo?highlight=%28root%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28root%29")
> To run a program using sudo that normally is run as the user, such as gedit, press Alt+F2 and enter gksudo gedit.

For users of Kubuntu, use kdesu in replacement for gksudo.
...
NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

Can anyone confirm this?

Azz, you seem to be saying sudo is fine from the command line both for graphical and non graphical apps. 

Cheers,

---

### Post by aysiu on 2006-10-09
*sudo* is not fine at the command-line for both graphical and non-graphical applications.

It's fine for non-graphical and *most* graphical applications.

To be on the safe side, always use *gksudo* or *kdesu* for graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by eeried on 2006-10-10
Many thanks for the link, aysiu.

Actually I know this psychocats.net Web site and enjoyed the howto install Xubuntu from Ubuntu. Yet I'd missed that sudo/gksudo page.

:)

---

