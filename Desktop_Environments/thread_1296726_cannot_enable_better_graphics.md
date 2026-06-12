---
title: "cannot enable better graphics"
date: 2009-10-21
forum: Desktop Environments
---

### Post by theshorthalf on 2009-10-21
I tried to enable the option for better desktop effects, but every time I do it, it comes up with a box saying "effects could not be enabled". 
Can someone please help me fix this? (note: complete linux newbie, only just installed today!)

---

### Post by theshorthalf on 2009-10-21
woops, sorry! Should have noticed the existing thread that troubleshoots this :oops:

---

### Post by raprap30 on 2009-10-21
It is because you did not install your hardware driver.

---

### Post by theshorthalf on 2009-10-21
I installed ubuntu yesterday, and when I tried to enable the better graphics effects it wouldn't work ("could not enable effects"). I then tried to run the compiz-check but it doesn't seem to be able to connect to the site:

caitlin@caitlin-laptop:~$ wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check
--2009-10-23 10:46:55--  [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download)
Resolving blogage.de... 188.40.53.170
Connecting to blogage.de|188.40.53.170|:80... failed: Connection timed out.
Retrying.

--2009-10-23 10:50:05--  (try: 2)  [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download)
Connecting to blogage.de|188.40.53.170|:80... 


Can someone please help me? I am connected through a proxy server that requires a username and password, so I don't know if that might be the problem? Or else maybe I'm just not using the terminal right, it's my first time using it. Any help would be much appreciated :)

---

### Post by overdrank on 2009-10-21
Hi and welcome, What is the model of the graphics card and have you installed the drivers for it? What version of ubuntu are you using? This can be found under system, about Ubuntu.
To identify your graphics card you can use the command in the terminal
```
lspci | grep VGA
```
The terminal is located under applications, accessories.
You may also look under system, administration, hardware drivers to see if any drivers are available for your graphics. 
Threads merged. :)

---

### Post by undecim on 2009-10-21
> **theshorthalf said:**
> I am connected through a proxy server that requires a username and password
That would be your problem. Here are some instructions I found to fix it: [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

You may also want to apply the instructions for the command line option as well, because that will tell any commands you use in the terminal to also use the proxy server.

After that, click the "Reload" button in synaptic package manager, check System -> Administration -> Hardware Drivers to see if you have any hardware drivers you can install.

Then install updates with System -> Administration -> Update Manager (your first set of updates will be very large! You may want to skip this step for now and leave that installing overnight)

EDIT: Btw, just in case you don't know, the "Synaptic Package Manager" that those instructions are referring to is located in System -> Administration

---

### Post by g160689 on 2009-10-22
go to system>hardware driver.
activate the graphics driver
if it doesnt work install necessary package

---

### Post by leverettson on 2009-10-22
As others have alluded to, it's all about what graphics card you have in your system. I've had better luck with Nvidia than ATI cards. Your really stuck until you can run lspci from a terminal to figure out what card is in the machine or just crack the box and take a look at the video card itself for labels etc. I'm hoping you have an Nvidia geforce 5200 or better.

---

### Post by theshorthalf on 2009-11-17
Hi,

Tried compiz-check, it told me that I had a problem with my graphics card and that it is blacklisted. 

I put in the command to find my graphics card and got this back:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Not sure what version of NVIDIA it is, hopefully someone can tell from the above? :S

Thanks heaps for the help!


p.s. my ubuntu version is Jaunty Jackalope 9.04

---

### Post by raprap30 on 2009-11-17
> **theshorthalf said:**
> Hi,

Tried compiz-check, it told me that I had a problem with my graphics card and that it is blacklisted. 

I put in the command to find my graphics card and got this back:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Not sure what version of NVIDIA it is, hopefully someone can tell from the above? :S

Thanks heaps for the help!




p.s. my ubuntu version is Jaunty Jackalope 9.04

NVIDIA is a brand of graphics card. It is evident that you have an Intel Graphics Card, not a NVIDIA one. Thus, try to find the graphics drivers for your model of graphics card, most specifically- Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). Dont be surprised that Compiz/Visual Effects will not work as your graphics card is a low-end one. But nevertheless, its worth the try!

---

### Post by realzippy on 2009-11-17
> **theshorthalf said:**
> Hi,

Tried compiz-check, it told me that I had a problem with my graphics card and that it is blacklisted. 

I put in the command to find my graphics card and got this back:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Not sure what version of NVIDIA it is, hopefully someone can tell from the above? :S

Thanks heaps for the help!


p.s. my ubuntu version is Jaunty Jackalope 9.04

Your Intel videocard is blacklisted due to huge problems in 9.04
with Intel.Install the newest ubuntu9.10,
where it is reported that the "intel" problem is solved..

---

