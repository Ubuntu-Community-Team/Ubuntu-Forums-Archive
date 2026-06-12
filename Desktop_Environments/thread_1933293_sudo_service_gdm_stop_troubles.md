---
title: "sudo service gdm stop troubles"
date: 2012-02-29
forum: Desktop Environments
---

### Post by 2MT350 on 2012-02-29
Hi all, I have setup a dual boot environment with windows and linux ubuntu 10.04.
everything seems to work ok exzcept for the command to stop the X server.

when i enter sudo service gdm stop into the console, it hangs, is there any way to fix this besides reinstalling? cause i've already tried to re install several times.

---

### Post by enjoijesus94 on 2012-02-29
Try This 

```
sudo /etc/init.d/gdm stop
```are you having trouble with ubuntu coming up after you select it at grub screen?

---

### Post by 2MT350 on 2012-02-29
Nah, Ubuntu seems to load fine, it loads nice, and faster then my current windows xp pro install.

i'll try that command, hope it works for me

---

### Post by enjoijesus94 on 2012-02-29
> **2MT350 said:**
> Nah, Ubuntu seems to load fine, it loads nice, and faster then my current windows xp pro install.

i'll try that command, hope it works for me

alright man.

Why do you wanna stop gdm?

---

### Post by 2MT350 on 2012-02-29
according to what i've read, i need to stop gdm to install the nvidia drivers :)

edit: your command didnt work enjo :(

---

### Post by enjoijesus94 on 2012-02-29
> **2MT350 said:**
> according to what i've read, i need to stop gdm to install the nvidia drivers :)

edit: your command didnt work enjo :(

aaaah i know how to do this 

ill give you a link to a post i made ok 

[http://ubuntuforums.org/showthread.php?t=1931109](http://ubuntuforums.org/showthread.php?t=1931109)

this is how to do it. 
if this dosnt help ill be sure to help you

---

### Post by 2MT350 on 2012-02-29
this part doesnt seem to be working for me

> gksu gedit /etc/modprobe.d/blacklist.conf

edit: the file grub.cfg seems to hold the blacklist settings now, but ubuntu wont let me edit it and save.

---

### Post by enjoijesus94 on 2012-02-29
> **2MT350 said:**
> this part doesnt seem to be working for me



edit: the file grub.cfg seems to hold the blacklist settings now, but ubuntu wont let me edit it and save.

try this 

```
gksudo gedit /etc/modprobe.d/blacklist.conf 
```

go to the very bottom and blacklist the drivers within the tutorial.

---

### Post by 2MT350 on 2012-02-29
that worked, thanks :D

---

### Post by enjoijesus94 on 2012-02-29
> **2MT350 said:**
> that worked, thanks :D

good good 
so all you gotta do is install the NVIDIA driver.

---

### Post by 2MT350 on 2012-02-29
i must be getting somewhere, but its still stopping, it shows ubuntu with 4 text dots under it, and thats where it stops when i try to stop xorg

---

### Post by enjoijesus94 on 2012-02-29
ok when it comes up to that screen press 

ctrl + alt + F4

when that happens login.

then stop GDM.

```
sudo /etc/init.d/gdm stop
```

next cd the driver you downloaded from the website.

```
cd /home/username/Downloads/yourdriver
```

then run 

```
sudo sh thepathtoyourdriver
```

after that start GDM

```
sudo /etc/init.d/gdm start
```

then start your interface

```
startx
```

---

### Post by 2MT350 on 2012-02-29
ah, it worked, thanks, i was trying to stop gdm with the x server console. i didnt know it couldnt be done thru that, my driver is fully operational :D now to adjust my settings, cause i think its at a higher resolution then im used to :)

thanks for your help, i finally learned a bit on how to work this OS :D

---

### Post by enjoijesus94 on 2012-02-29
no problem at all 

so you got everything installed?

and you need anything just post:guitar:

---

### Post by 2MT350 on 2012-02-29
yep, everything i needed to do is done,  no troubles now :)

---

### Post by enjoijesus94 on 2012-02-29
> **2MT350 said:**
> yep, everything i needed to do is done,  no troubles now :)
glad it worked 
:popcorn:

---

### Post by 2MT350 on 2012-02-29
yea, same here, :popcorn:

---

