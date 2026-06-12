---
title: "I'm sooo green (Remote desktop)"
date: 2009-02-18
forum: General Help
---

### Post by Intelli32 on 2009-02-18
I installed Ubuntu 8.10 yesterday and this is my first time using this OS.
I need help with installing some kind of Remote Desktop server on this computer (Ubuntu 8.10) and I need to access it from a computer with **WINDOWS XP**

I tried installing FreeNX but it did not work out, I have no idea on how to actually connect to my Ubuntu computer. I have heard that VNC is supposed to be easier to install and work with?

**_I want to:_**

- Access my Ubuntu computer (this will be used as a file-server) from a WinXP computer
- Be able to *control* my Ubuntu computer

**_My knowledge:_**

- Absolutely NONE! I dont know any Terminal codes. I can barely install applications. I had to guess which file to start when I installed FreeNX.


This seem like a very friendly and helpful community. Please dont blow me off, please give instructions and/or refer me to some sort of USERFRIENDLY guide. As stated, I dont know ANY technical term or shortening. Please be descriptive.

Cheers ;)

---

### Post by HermanAB on 2009-02-18
In plain English, you need to install openssh-server on Linux and run the sshd server.

On Windows, install Xming and PuTTY (Google for Xming, they have a link to PuTTY).  Run Xming first, then PuTTY and enable X forwarding in PuTTY.  Then you can connect to the Linux machine and run gnome-panel.  Once the panel comes up on Windows, you can go click happy and run any Linux program remotely.

Cheers,

Herman

---

### Post by heindsight on 2009-02-18
Ubuntu already has a VNC server installed by default. You can activate it by going to System>Preferences>Remote Desktop
There you have to enable the options: "Allow other users to view your desktop" and "Allow other users to control your desktop". It may be a good idea to also enable the security options which require you to give permission before anyone can connect or require that users enter a password before connecting.

I don't know exactly how you'd connect from a windows machine, but you'd need a VNC viewer installed which you'd have to use to connect to port 5900 on your ubuntu machine.

EDIT:
you may want to do a google search for "ubuntu remote desktop" (without the quotes). In particular I'd recommend reading this:[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by Intelli32 on 2009-02-18
Okay guys! Thanks for your fast response. I will look into both of these solutions and see which one I manage to install.

I would love to hear more, if there is other solutions so keep 'em comming!

Cheers again! :p

---

### Post by Intelli32 on 2009-02-18
Ah, this is awesome! Soooo much faster than the FreeNX installation. I actually using the Remote Desktop while writing!

Thank you all for your input! You all have a good night (atleast its night here in Sweden)

:D

---

### Post by heindsight on 2009-02-18
Btw. If you want to access files on your ubuntu machine from a windows machine, you may want to have a look at samba. Read this: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) and [https://help.ubuntu.com/8.10/serverguide/C/windows-networking.html](https://help.ubuntu.com/8.10/serverguide/C/windows-networking.html)

---

### Post by Intelli32 on 2009-02-18
Oh yeah! I heard about that. That is what this whole experiment is about. I am creating a File/FTP server. 

Thanks!

---

