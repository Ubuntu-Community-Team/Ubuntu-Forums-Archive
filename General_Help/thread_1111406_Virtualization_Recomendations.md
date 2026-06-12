---
title: "Virtualization Recomendations"
date: 2009-03-30
forum: General Help
---

### Post by makaymurray on 2009-03-30
Hey fello linux geeks out there:

I am very interested in Virtualization for my buisness but am overwhelmed with the amount of choice I have pertaining to what virtualization software to use. Any recomendations welcome. 

I have a fairly small server deployment with a "HP Proliant DL140" and two "HP Proliant ML350". Each server is running a dedicated application nessisary for the operation of my office. within the next months I will be expanding into a adjasent office space and a space accross the street. I do not wish to buy additional servers if I dont need to. (note: the three apps are a client database, a image database and a 3d image database. so very rarely do i have large files being transfered)

also im running Microsoft XP Pro on every system.


any help would be appreshiated. thank you in advance.

---

### Post by ibuclaw on 2009-03-30
If you are wanting to run Linux Servers, the best I know of is OpenVZ, which allows you to run Linux ontop of Linux in "containers", all using the same resources, and can be given their own IP addresses.

If in doubt, VMWare is a really good virtualisation software to use. I wasn't impressed by VMWare2.0 and **their** web-based administration kit (was very slow), but you may find its pros outway the cons of it.

Regards
Iain

---

### Post by makaymurray on 2009-03-30
is it possible to run windows XP Pro as a virtual machine inside of a linux server. 

its not that im in love with windows (im not) its just that the applications i need to run are windows only.

---

### Post by bodhi.zazen on 2009-03-30
You can run windows.

I suggest you look at KVM or VMware. You can look at VirtualBox as well, but you probably can not use it (VBox) for what you envision, read the liscence.

---

### Post by arrrghhh on 2009-03-30
There are a lot of options, but that's one of the best things about Linux!  Choice!  At any rate, I'd recommend VirtualBox.  Despite the last post - you CAN use VirtualBox - so long as you use the OSS edition in the repo's as opposed to the precompiled binaries on their site (you miss stuff like vRDP, USB support, etc).  So long as you don't need USB (or anything else the open source version is missing) then I'd say that would be your best bet.  The easiest to setup (by far, IMHO) and probably the easiest to use (again, IMHO).  ESX-i is awesome, but WAY more than you need.  Plus I think the Infrastructure client is where they get you ($$$).  At any rate, give VirtualBox a shot, but use the OSS version if it's for a business!

---

