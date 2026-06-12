---
title: "how to remove edubuntu"
date: 2013-02-11
forum: Desktop Environments
---

### Post by stephenbbb on 2013-02-11
how can I remove edubuntu??

I installed edubuntu 12.04 thinking it would have more educational software than Ubuntu. it does not or it is so messy to use it I don't know how.
anyway I want to remove it now and did

sudo apt-get remove edubuntu-desktop

well it is still there, when the box restarts I see "edubuntu 12.04" instead of "ubuntu 12.04". 

thanks everybody.

---

### Post by ibjsb4 on 2013-02-11
Try this

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by stephenbbb on 2013-02-11
that is a bit of overkill especially given that I need some of the python packages on that list. I just did:

scb@scb-desktop:~$  sudo apt-get remove edubuntu-artwork edubuntu-desktop edubuntu-docs edubuntu-fonts edubuntu-menueditor 

scb@scb-desktop:~$ sudo apt-get autoremove

scb@scb-desktop:~$ sudo apt-get install ubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Now the question: in the list I saw ubuntu-edu-primary which is what I needed in the first place for my kids. Do you know how to use that and what are the applications in it??

Thanks a lot

---

### Post by Frogs Hair on 2013-02-11
I got a list of recommended for installation from the synaptic package manager. You can look up the individual programs in the software center. No list was found on the website.

---

### Post by zombifier25 on 2013-02-12
Installing the edubuntu-edu-primary package should pull in all of its program.

---

### Post by stephenbbb on 2013-02-12
> **Frogs Hair said:**
> I got a list of recommended for installation from the synaptic package manager. You can look up the individual programs in the software center. No list was found on the website.
to Frogs Hair:
where is the software center?? also the synaptic manager is gone in 12.04.

---

### Post by Frogs Hair on 2013-02-12
If you are using Unity simply type software center in dash and the icon will appear. It is also one of the default launchers in the panel unless removed.

Synaptic is no longer a default application but is in the software center. The primary bundle is also in the software center but I only found the application list in synaptic.  

```
sudo apt-get install synaptic
``` 

Type synaptic in dash

---

