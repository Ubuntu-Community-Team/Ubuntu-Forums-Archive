---
title: "Help needed please!!! Installing kde desktop on ubuntu server"
date: 2009-02-14
forum: General Help
---

### Post by aiden707 on 2009-02-14
hi 
i am new to linux and i had installed ubuntu server then put the ubuntu desktop on, but i would prefer kde4 desktop. so i did a new insatall of ubuntu server 64 bit (with samba loaded) and then did this:--

sudo aptitude update
sudo aptitude install kubuntu-kde4-desktop

all was going well but i got this message:

leave the following dependencies unresolved.
python-reportlabs recomends python-renderpm
score is 30
y or n

i typed yes and the install contined well but when i try to log on it just freezes after i loged in (get small black square with a hard drive in it ) then returns to the log in screen.
please can someone help as is driving me nuts and i sure kde4 be a better desktop for me to learn on cos i was a windows user before.
thanks
aiden

---

### Post by hyper_ch on 2009-02-14
why do you want to install a desktop onto a server?

What do you want to use the server for anyway?

---

### Post by aiden707 on 2009-02-14
i want the server hold files and back up my other home pc (all windows) , and maybe even controll the internet access , i new to linux so wanted a desktop to help learn lynix before i start useing just the command lines on the server.

---

### Post by hyper_ch on 2009-02-14
why don't you install then from the desktop or alternate cd and add server things later?

---

### Post by aiden707 on 2009-02-14
if i install desktop first  will it be ok as a home server?

---

### Post by hyper_ch on 2009-02-14
there are two main differences between server and desktop isntall

(1) on the server there are only minimal packages and no gui installed

(2) the server uses a different kernel which is optimized for server tasks

You can install apache, samba, ssh server, email server, ..... on a desktop install also.

HOWEVER: If you really want to run a server you want to install as little as possible. You don't want any packages you don't need. You don't want to have a gui running all the time. One reason is security and another is performance. The server install given by Ubuntu is aimed as minimal stable install for businesses and stuff. You don't need a gui to run the server. All you need is a way to login into the CLI and manage the server from there (or using Webmin for a web based aministration interface).

However I'd rather suggest to first give it a go all through CLI. You find plenty of information on how to install the individual parts and configure them.

All you need to know is:

(1) how to login into the server cli
(2) move along the filesystem directory
(3) manipulate file
(4) control the services (start/stop/restart)
(5) install software

For those 5 things you don't need to have much knowledge :)

---

### Post by aiden707 on 2009-02-14
sounds like i want try a little more with just the cli,
i can log in and see directories (with windows i am ok at useing the command line) i have found a site with all the bash cli commands so can learn more there.
i have 2 NIC one for the internet and one that i wanted to form my home network .can you help to exsplain how i get the server to broadcast a ssid i can see on my windows client pc?i have samba installed.
thanks

---

### Post by aiden707 on 2009-02-14
should of mentioned the NIC cards i have one is LAN (internet) the other is a wireless NIC

---

### Post by hyper_ch on 2009-02-14
a few things:

(1) Cheat sheets

Print that one out:  [http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/) (it's a pdf=
Also this one, as this is more aimed at the CLI: [http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

(2) have a look at the man pages. Often they have very, very much information.
```

man PROGRAM

```

e.g.

```

man nano

```

(3) Use google - this solves also lots and lots of problems

(4) If you still have problems, ask here in the forums.

---

### Post by aiden707 on 2009-02-14
thanks a lot for the links, i going learn the cli and keep with a server with no GUI
cheers 
aiden

---

### Post by hyper_ch on 2009-02-14
it will take some time but just do one thing after the other. There's plenty of guides out there. A good way to start would probably be [http://www.howtoforge.com](http://www.howtoforge.com)

---

