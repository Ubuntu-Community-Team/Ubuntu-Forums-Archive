---
title: "GUI won't start"
date: 2009-04-30
forum: General Help
---

### Post by little_foot on 2009-04-30
Running xubuntu 8.10, computer froze and had to restart, but will not restart or load GUI only command line.

startx gives:

(EE) Failed to load module "versa" (module does not exist, 0)
(EE) No drivers available

Fatal server error:
no screens found
giving up.
xinit: connection failed (errno 111): unable to connect to X server
xinit: no such proccess (errno 3): Server error


----------

I tried:
apt-get install xubuntu-desktop, but says already have the latest version
also tried, dpkg-reconfigure xserver-xorg
But that does work either

Help

---

### Post by skymera on 2009-04-30
What is your graphics card?

---

### Post by little_foot on 2009-04-30
not sure, it is a Dell Inspiron 1100

---

### Post by little_foot on 2009-04-30
I think intel  GMA X4500MHD [I]graphics card

[/I]

---

### Post by little_foot on 2009-04-30
Cnet says:

                                 	 		Intel Extreme Graphics

---

### Post by little_foot on 2009-04-30
reloaded my backup copy of /etc/X11/xorg.conf

but that didn't seem to help either and it was the one I have been using for awhile now on xubuntu 8.4

---

### Post by x1a4 on 2009-04-30
Hi,

As the error states, you're trying to load a non-existent module: versa.  Were you trying to load the vesa drivers?  Look in your xorg.conf file in the  "Module" section and either replace versa with vesa or remove that line.  

Hope this helps.

---

