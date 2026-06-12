---
title: "setup vnc server"
date: 2006-05-18
forum: Desktop Environments
---

### Post by resnostyle on 2006-05-18
i was in the process of following the guide presented.. 
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

i got to sudo dpkg -i vnc4server_4.0-7.3_amd64.deb a

and when i execute that i get dpkg: status database area is locked by another process. 

any idea what the other process is? and how to fix it?](*,)

---

### Post by aysiu on 2006-05-18
Anything wrong with System > Preferences > Remote Desktop?

---

### Post by aysiu on 2006-05-18
[QUOTE=resnostyle]
i got to sudo dpkg -i vnc4server_4.0-7.3_amd64.deb a

and when i execute that i get dpkg: status database area is locked by another process. 

any idea what the other process is? and how to fix it?](*,)[/QUOTE] It's probably you having Synaptic Package Manager or Add/Remove Applications open.

---

### Post by resnostyle on 2006-05-18
[QUOTE=aysiu]Anything wrong with System > Preferences > Remote Desktop?[/QUOTE]

ok i tried that but how would i be able to access it with a windows xp machine?

---

### Post by aysiu on 2006-05-18
[QUOTE=resnostyle]ok i tried that but how would i be able to access it with a windows xp machine?[/QUOTE] Three things: 

1. Create a password in the preferences for Remote Desktop
2. Paste this command into a terminal to find out your IP address: ```
ifconfig
```
3. Install TightVNC on Windows and launch TightVNC Viewer (Best Compression). For the server name, type the IP address. For the password, type the password you defined earlier.

---

### Post by resnostyle on 2006-05-18
hey thanks alot

---

### Post by resnostyle on 2006-05-18
is there a way to allow it auto accept a connection instead of accepting it on the machine?

---

### Post by aysiu on 2006-05-18
[QUOTE=resnostyle]is there a way to allow it auto accept a connection instead of accepting it on the machine?[/QUOTE] Yes, that should be one of the configuration options when you go to System > Preferences > Remote Desktop

Uncheck the box that says you need a confirmation.

---

### Post by melchior on 2006-05-19
[QUOTE=aysiu]Anything wrong with System > Preferences > Remote Desktop?[/QUOTE]
It's slooooow! even across LAN. Freenx flies, but of course will not pick up the open session. I have been unsuccessful in replacing vino with another server that does the same thing.... any help?

---

