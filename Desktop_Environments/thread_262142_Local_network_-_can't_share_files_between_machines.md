---
title: "Local network - can't share files between machines"
date: 2006-09-21
forum: Desktop Environments
---

### Post by okok on 2006-09-21
I have two machines, both running the latest Ubuntu, both connected to a wireless router and can access the internet and the router's control panel via its own IP number.

However, I don't understand how to share files between these two computers, how to allow each one of them access the other. I read the relevant information on the ubuntu wiki, but failed to make it work.

I would be grateful for hints, or better - step by step instructions.

---

### Post by kidders on 2006-09-21
Hi there,

Step one is to decide what kind of filesharing protocol you want to use. There are lots of options, but three common choices are Windoze filesharing, Apple filesharing and NFS. Which one you pick is down to personal choice, but you'll need to install the necessary software to serve shared files in any case.

---

### Post by wpshooter on 2006-09-21
Probably goto file sharing under administration and check and then install SAMBA.  Make sure you name the shares on each machine with an identifying name that is unique to each machine.

---

### Post by kidders on 2006-09-21
Something to be aware of with Samba is that using it would make you subject to all the idiotic restrictions Windows filesharing places on users, such as what you can call files, who owns them, what access permissions they're able to have, and so on. It can also be a little slow ... although, if you're using WLAN, you don't care about speed!

If there aren't any Windows machines on your network, Samba is a bad choice. As wpshooter will tell you, most people do though :-)

---

### Post by beerfan on 2006-09-21
I recommend installing SSH on both machines. This will allow you to use GnomeVFS (the "Places" > "Connect to server" menu option) to create secure connections to any path you like. Samba really isn't necessary or even desirable unless you have windows machines.

---

### Post by spacey on 2006-09-22
i have two computers both running ubuntu and do not need to share with windows users, can anybody give me a link to a step to step guide. I tried, oh god how i tried but keeps ******* it up.

---

### Post by kidders on 2006-09-22
Try using NFS ... it's straightforward enough.

Just install a server, add a line or two to /etc/exports, start the service and away you go.

---

