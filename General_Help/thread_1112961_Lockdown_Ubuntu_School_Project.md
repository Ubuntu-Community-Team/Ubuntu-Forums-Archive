---
title: "Lockdown Ubuntu School Project"
date: 2009-04-01
forum: General Help
---

### Post by Sastra on 2009-04-01
Hi,

I have a question, for a school project I need to lockdown Ubuntu as far as possible, and make it as easy as possible for people to use.
The most use full tip I found on this forum was to disable Nautilus as the service responsible for the desktop. I did this using Gconf-editor. 
This all works great, people can't right click anymore. However Auto-mount doesn't work anymore if I disable Nautilus as the " desktop" service. The only way to auto-mount a DVD, USB Stick etc. is to open up Nautilus and let it mount the device. But the idea of the project was to make it as "simple" as possible, so this doesn't fit in the whole idea ;)

So my question is, is there a way to resolve this issue? Maybe let Nautilus run as a "background" service? Or disable the entire right mouse butten? Or let the left and right mouse do the same functions? 

Or is this a big limitation of Gnome?

Thanks in advance :D

---

### Post by aeiah on 2009-04-01
what will they be using it for? why do you have to use gnome?

---

### Post by 24*7 on 2009-04-01
If u could mention the **exact set of features that you want to disable** for the users, u can get a better reply. 

Why don't u just use a **limited account or Guest account**?? Does this type of account not solve ur requirement?

---

### Post by Yashiro on 2009-04-01
You might need to look into the Authorizations menu item.

Additionally you might want to look at Fedora. It's slightly more workplace orientated and has more options for management and lockdown.

---

### Post by Sastra on 2009-04-01
The following functions are needed: 

- Watching DVD movies
- Listening to Audio CD`s
- OpenOffice
- Internet (I locked Firefox down using Stylish with a Kiosk template)

But after some research I found a way to completely disable the right mouse button.. And for as far as I can see at the moment, this "dirty" trick seems to do the job for me ;)

---

