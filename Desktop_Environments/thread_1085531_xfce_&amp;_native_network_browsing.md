---
title: "xfce &amp; native network browsing"
date: 2009-03-03
forum: Desktop Environments
---

### Post by sartic on 2009-03-03
I tried Xubuntu after more than year. Still has no native network browsing?! On my test system is more memory hungry than gnome tweaked (compiz, tracker and some process out) but desktop is faster than gnome. Your impressions ... love to hear.

---

### Post by sartic on 2009-05-02
Is there any progress in this point for Jaunty release?

---

### Post by DavidTangye on 2009-05-02
By 'native' network browsing, if you mean in the file manager that is included with Xubuntu (thunar), I do not think there is any plan to add network browsing into it. I use Midnight Commander, and its ssh virtual file system to copy files from network shares. To do this:
 * Define login accounts on server machines as usual, and ensure sshd is installed and the service is running
 * On those (client) machines you want to use to access those shares:
  -  Its helpful to add the servers' ip and hostnames in the client's /etc/hosts
  - Test you can ssh to the server: In a terminal run 'ssh -X username@ServerHostOrIPaddress'
  - Install Midnight Commander with Synaptic
  - Start Midnight Commander in a terminal (command = 'mc'), then
     F9 Left or Right panel, 'Shell Link', enter username@ServerHostOrIPaddress, enter the password (its at the bottom of MC). You should get the directory of / on the server.
     Save the link for future use with Ctl-X,H
     Navigate directories by highlighting them and hit Enter.
     Copy with F5, Move with F6, files from one panel to the other panel, ie machine to machine
     Save useful directories as more links for future use with Ctl-X,H

---

### Post by jlimon on 2009-05-03
I never understood the need/want for VFS access to NFS/Samba/SSHFS when you can just mount them with fstab and have better access to the files.

If you "need" a VFS method to access your files you can use Gigolo..

---

### Post by sartic on 2009-05-04
Didn't know about Gigolo. I will try next time...
Today is must network browsing for OS. If I need faster desktop LXDE and E16 is what I use today on low end machines.
I aged on Volkov/Far/Gyula/Gnome Commander but today most of time I use Nautilus width tabed interface.

---

