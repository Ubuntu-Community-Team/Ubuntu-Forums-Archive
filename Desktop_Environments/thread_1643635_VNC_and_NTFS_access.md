---
title: "VNC and NTFS access"
date: 2010-12-12
forum: Desktop Environments
---

### Post by xendistar on 2010-12-12
I have just done a new installation of 10.10 Xubuntu onto the wife PC which dual boots with win XP and have a couple of problems. The first is I can't access the 2nd harddisk in the PC, (it is a window XP NTFS drive, one partition, xubuntu is on the other hard disk). I have the ntfs packages installed to be able to access the drive

Secondly I have installed tightvnc on to the PC and started the vncserver with the follwing command

vncserver -geometry 1024x768 -depth 24 :1

It asked me to set a password to access the desktop which I did but when I try to access the PC via VNC over the local lan I get Connection failed. I tried accessing the wife PC from two different PC's (one linux one windows) both on the same lan and the results are the same. On the windows PC I am using the tightvnc client which I know works as I use it to make a vnc connection to a different PC. If I enter the vnc start command again it tells me that the server is already running.

Can anybody advise on either problem?

---

### Post by Ogatai on 2010-12-12
> **xendistar said:**
> I have just done a new installation of 10.10 Xubuntu onto the wife PC which dual boots with win XP and have a couple of problems. **The first is I can't access the 2nd hardisk in the PC**, (it is a window XP NTFS drive, one partition, xubuntu is on the other hard disk). I have the ntfs packages installed to be able to access the drive

Secondly I have installed tightvnc on to the PC and started the vncserver with the follwing command

vncserver -geometry 1024x768 -depth 24 :1

It asked me to set a password to access the desktop which I did but when I try to access the PC via VNC over the local lan I get Connection failed. I tried accessing the wife PC from two different PC's (one linux one windows) both on the same lan and the results are the same. On the windows PC I am using the tightvnc client which I know works as I use it to make a vnc connection to a different PC. If I enter the vnc start command again it tells me that the server is already running.

Can anybody advise on either problem?

Hi, i had the exact same problem when i installed Xubuntu from Ubuntu (trough synaptics), come here:
[http://ubuntuforums.org/showthread.php?t=1643100](http://ubuntuforums.org/showthread.php?t=1643100)
it works excellent...
about the VNC thing, sorry but i got nothing...

---

### Post by Jose Catre-Vandis on 2010-12-12
Try installing **remmina** to use as a vnc client, see if that resolves issues

---

### Post by xendistar on 2010-12-12
Thanks Ogatai, that resolved my ntfs problem, now just the VNC to go............

---

### Post by xendistar on 2010-12-12
> **Jose Catre-Vandis said:**
> Try installing **remmina** to use as a vnc client, see if that resolves issues

Unfortunately the linux PC I am using is not a buntu based and remmina is not available.

As it is I was having a blonde moment and have resolved that particular problem (I forgot to add the :1 to the IP address when I tried to connect).

Problem is now the desktop window comes up but instead of the desktop I get a grey square (1024 x 768 sized, I get a mouse cursor that move, but that is about it.

Tim

---

### Post by Jose Catre-Vandis on 2010-12-12
> **xendistar said:**
> Unfortunately the linux PC I am using is not a buntu based and remmina is not available.

As it is I was having a blonde moment and have resolved that particular problem (I forgot to add the :1 to the IP address when I tried to connect).

Problem is now the desktop window comes up but instead of the desktop I get a grey square (1024 x 768 sized, I get a mouse cursor that move, but that is about it.

Tim

[http://sourceforge.net/projects/remmina/](http://sourceforge.net/projects/remmina/)

---

### Post by xendistar on 2010-12-12
OK I am going to mark this as resolved now as I have been able to set up a connection,maybe not the ideal way but at least I am able to access the PC.

I think the main problem was that I was starting the vnc server logged in as the wife (it is her PC), but if I ssh-ed into the PC and then logged on as me and then started vncserver I am able to make a connection. As I said maybe not the best way but this is only a short term thing and I went for something I knew as opposed to many other option that I have never played with.

Thanks for all the advice

Tim

---

