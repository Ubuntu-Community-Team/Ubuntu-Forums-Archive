---
title: "iTunes"
date: 2006-06-17
forum: Desktop Environments
---

### Post by dareofficer on 2006-06-17
I have a Mac running Tiger with a lot of music on it.  I have in my bedroom a linux system.  How can I link from my linux system to the Mac iTunes files?
:confused:

---

### Post by aysiu on 2006-06-17
Do you want to link to the *files* or do you want to be able to access iTunes shares?

---

### Post by dareofficer on 2006-06-17
I want to have a link from my linux system to the Mac.  Is that possible?

---

### Post by raptros-v76 on 2006-06-17
you cant just link between two systems. you need a method of transport. do you wnat to use itunes music share? i mean besides samba, i dont have any suggestions.

---

### Post by dareofficer on 2006-06-17
I just want to use the Mac as a music server.  Would this be better to put the musci on the Linux machine and use it as a server?  I would like one computer with the music and my other computers being able to open the music up as a file server if possible?

I can FTP into my Mac no problem with Ubuntu.  My problem is being able so see my Ubuntu from my mac????  I'm very lost:-(

---

### Post by raptros-v76 on 2006-06-17
did you set up a server of some kind for your ubuntu? try using an apache server, and stream music from your ubuntu computer.

---

### Post by dareofficer on 2006-06-17
Could you help me with that?  How do you set that up?

---

### Post by dareofficer on 2006-06-17
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

What does this mean?  I have been trying to install the server?

---

### Post by raptros-v76 on 2006-06-17
install it:
```
sudo aptitude install apache
```
then the configuration file is /etc/apache/httpd.conf
make sure that things are readable, nothing is writable
then 
```
 sudo ln -s <path to your music folder> /var/www/ 
```

---

### Post by dareofficer on 2006-06-17
Works PERFECT!!  Thanks!:KS :D

---

### Post by raptros-v76 on 2006-06-17
see, apache is the thing i love most about open source software. it works, it gives you an http server in almost no time with no sweat.

---

