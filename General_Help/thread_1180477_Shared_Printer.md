---
title: "Shared Printer"
date: 2009-06-06
forum: General Help
---

### Post by dbdsol on 2009-06-06
Hello, 

I'm new to Linux, Ubuntu and this forum so please bare with me! I just spent 45 minutes trying to search for an answer to my problem, but hopefully someone has some wisdom for me.

I have a Lexmark 3650 Multi-Printer and I realize that it will not work with ubuntu. I have a seperate computer running Windows XP and I just hooked the printer up to it and shared it. 

I figured this way theres no need for a driver, but I'm mistaken apparently. When I try to install it as a network printer it still wants a driver on my Ubuntu box.

Know of anyway to get around this? Thanks in advance.

---

### Post by dbdsol on 2009-06-06
bump

---

### Post by rcayea on 2009-06-06
I had the most frustrating experience with my HP printer until...

I came across someones post who said go to the HP company website and look at their Linux information. I checked it out and they have all kinds of info about how to setup printer for Linux.

My point is, maybe give the Lexmark company website a try and search there. 

Good luck,
Randy

---

### Post by dbdsol on 2009-06-06
> **rcayea said:**
> I had the most frustrating experience with my HP printer until...

I came across someones post who said go to the HP company website and look at their Linux information. I checked it out and they have all kinds of info about how to setup printer for Linux.

My point is, maybe give the Lexmark company website a try and search there. 

Good luck,
Randy

Yeah I gave Lexmark a try....no such luck...

I've given up on finding a driver, I'm just trying to find a way to use the printer over the network without any driver on my Ubuntu machine.

---

### Post by rcayea on 2009-06-06
I came across this site with a google search...

I didn't see your printer listed but they do have various linux drivers so I thought if you wanted you could sift through these pages.

[http://74.125.47.132/search?q=cache:vwdyoUoI3z8J:www.nodevice.com/driver/company/Lexmark/Printer.html+Linux+Lexmark+3650+Multi-Printer&cd=4&hl=en&ct=clnk&gl=us](http://74.125.47.132/search?q=cache:vwdyoUoI3z8J:www.nodevice.com/driver/company/Lexmark/Printer.html+Linux+Lexmark+3650+Multi-Printer&cd=4&hl=en&ct=clnk&gl=us)


I am searching with "Linux driver for Lexmark 3650" I will let you know if I come across anything

Also, have you try synaptic yet to see if anything is listed?

---

### Post by rcayea on 2009-06-06
More discussion at this site:


[http://www.linux-archive.org/ubuntu-user/230770-printer-copier-scanner-ubuntu.html](http://www.linux-archive.org/ubuntu-user/230770-printer-copier-scanner-ubuntu.html)

I promise not to post any other links unless they actually contain a driver for you.  :)

---

### Post by dbdsol on 2009-06-07
If you find it I will be amazed!  Thanks alot for extra set of eyes!

---

### Post by dbdsol on 2009-06-07
Well I didnt find the exact solution I was looking for but I did find a working solution.  

- As I said before I have a seperate box running Windows XP and the printer is physically hooked up to that machine.

- On my Ubuntu box I have VirtualBox running Windows XP.  Windows XP on VirtualBox cannot use the printer physically because it seems at this time that VirtualBox does not support USB printers.  However it can access the Network Printer attached to the Windows XP box.

---

