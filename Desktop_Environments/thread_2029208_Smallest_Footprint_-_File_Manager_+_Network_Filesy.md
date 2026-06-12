---
title: "Smallest Footprint - File Manager + Network Filesystem"
date: 2012-07-19
forum: Desktop Environments
---

### Post by dcuster on 2012-07-19
What can I install to accomplish accessing network filesystems with a file manager, using the smallest possible footprint?

Plz&Thx:popcorn:

---

### Post by critin on 2012-07-19
> **dcuster said:**
> What can I install to accomplish accessing network filesystems with a file manager, using the smallest possible footprint?

Plz&Thx:popcorn:

There are several--at the moment Samba is my choice.  It's simple file sharing that works.

---

### Post by dcuster on 2012-07-19
yea, but don't I have to use samba through the terminal? and not something like thunar.

---

### Post by sudodus on 2012-07-19
> **dcuster said:**
> yea, but don't I have to use samba through the terminal? and not something like thunar.
Once you have the file sharing service running, samba, ssh ..., you can use a file browser, Nautilus, Thunar, PcmanFM to connect from linux.

From Windows you can connect with the native browser (Explorer) via samba, and with WinSCP via ssh.

---

### Post by critin on 2012-07-19
> **dcuster said:**
> yea, but don't I have to use samba through the terminal? and not something like thunar.

No, you don't have to go through the terminal if you just want to share.   Go to the files you want to share and click on 'permissions'.  Give permissions and allow 'shares'.  The system will install samba for you.    You have to give permission to share for every folder/file that you want to share.  Not just once.  

Restart the machine.

Go to windows and set up the network sharing.  I disabled Windows firewall for the network and it worked smoother. 

You'll find your successful network in your ubuntu Home folder, along the left menu list.
There are some configurations to do so read all instructions carefully.

---

