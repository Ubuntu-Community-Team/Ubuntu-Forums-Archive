---
title: "Disable X11/Xorg"
date: 2010-09-12
forum: Desktop Environments
---

### Post by GrantStoner on 2010-09-12
In Ubuntu 10.04 (Lucid) how do I go about disabling X11 or Xorg or whatever, from starting automatically? I like the way BackTrack starts how you have to log in first, and then type "startx".

---

### Post by clrg on 2010-09-12
You need to edit /etc/init/gdm.conf, specifically the "start on" section, so it won't start automatically. I suggest you make a backup copy of the file first, in case you mess something up. After you made your changes, apply the configuration by running ```
sudo initctl reload-configuration
```

If you want to start Gnome after your system booted, run ```
sudo service gdm start
```

---

### Post by GrantStoner on 2010-09-12
Do I just change ```
start on
```to```
start off
```? Or what do you mean by editing? Or leave as ```
start on
``` and then edit what's in the parenthesis?

Edit: Nevermind, I just changed ```
on
``` to ```
off
```. And this starts me in tty1 this way.

---

### Post by GrantStoner on 2010-09-12
1) When I start in tty1, however, it doesn't seem to load everything it normally does? When I log in and then type ```
startx
``` it starts gnome, but then tells me keyrings and whatnot weren't started when I logged in. So I have to authenticate them individually?

2) Also, disabling gdm from starting automatically puts me in tty1, but doesn't let me see my system as it's loading. I'm looking more for like verbose-startup I suppose? I change my hardware quite frequently and I like to see the different adapters and whatnot as they're starting so I know everything is loading the way it should.

---

### Post by clrg on 2010-09-12
You need to change the grub configuration if you want to see startup messages. Edit /etc/default/grub and remove the "quiet" boot option. Then run ```
sudo update-grub
``` to apply the changes.

> **GrantStoner said:**
> When I start in tty1, however, it doesn't seem to load everything it normally does? When I log in and then type ```
startx
``` it starts gnome, but <...>

I said, use ```
sudo service gdm start
```.

---

### Post by GrantStoner on 2010-09-12
> **clrg said:**
> You need to change the grub configuration if you want to see startup messages. Edit /etc/default/grub and remove the "quiet" boot option. Then run ```
sudo update-grub
``` to apply the changes.
Thanks this worked exactly the way I wanted. I just put the "##" right in front of that option instead of editing/deleting the option.



> **clrg said:**
> I said, use ```
sudo service gdm start
```.
When I do this, all I get is ```
start: Unknown job: gdm
```This is why I do ```
startx
``` instead, and It works flawlessly, EXCEPT for the message that pops up and "Unlock Login Keyring" and says my keyring wasn't unlocked when I logged in.

---

### Post by DemonBob on 2010-09-12
If you are going to use startx command. You need to create a .xinitrc file in your home directory and have this in the file. 


```
#!/bin/sh
#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#
# exec ion
# exec jwm
# exec wmaker
# exec startkde
# exec icewm
# exec blackbox
exec gnome-session
# exec startfluxbox
# exec startxfce4
# exec xfce4-session
# exec openbox
# exec startlxde
```

---

### Post by GrantStoner on 2010-09-12
If I have the libraries installed for the other environments, do I just put the "#" back in front of ```
exec gnome-session
``` and erase the "#" from which ever I want to enable?

---

### Post by DemonBob on 2010-09-12
> **GrantStoner said:**
> If I have the libraries installed for the other environments, do I just put the "#" back in front of ```
exec gnome-session
``` and erase the "#" from which ever I want to enable?

Yup

---

### Post by GrantStoner on 2010-09-12
Thanks, I'm still getting the "Unlock Login Keyring" error though. I have everything in the "Startup Applications" checked. I thought maybe I didn't have one of the daemons set to start, but nope, they're all selected. Would I get this message if I'm really using KDE but have the gnome daemons on? How would I tell what environment I'm using? It looks like gnome, but it looks like KDE as well... like a KDE theme for gnome, or possibly a gnome theme for KDE.

---

