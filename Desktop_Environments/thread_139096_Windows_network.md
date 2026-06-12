---
title: "Windows network"
date: 2006-03-03
forum: Desktop Environments
---

### Post by fjcouto on 2006-03-03
Hello again !!

I've been using UBUNTU in the office (we also have a windows network) for 3 months  now.

Well, I don't know how I did it (probably un update or something I have installed)  but my problem is that Nautilus is not automaticaly "reading" my windows network (unless I tipe  smb:// machine IP). 

It used to work fine (I just had to click Network Servers in the local menu) but suddenly it stops reading it !

Can anybody help me ???

Many, many, many, TKS !!!

---

### Post by jamyskis on 2006-03-03
Try adding your local DNS server. I had this problem and it did the trick for me.

---

### Post by fjcouto on 2006-03-03
argh ... It did work ... but guess what ...

I have edited my etc/resolv.conf to put up an Names Server

domain "mydomain"
nameserver "IP address"

I can see the network now but every time I boot the system, Ubuntu edits my resolv.conf and the configuration is lost !!!! 

Do you know why the system is overwriting the resolv.conf everytime I boot ? Is that normal ? Is there anyway I can stop it from doing so ?

Many many tks again !!!

---

