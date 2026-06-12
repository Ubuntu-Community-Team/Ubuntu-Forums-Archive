---
title: "Compiz won't work"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by Kris001 on 2008-02-05
Hi everyone,
I've used Kubuntu for a few days now, works great!!
Now, I'm trying to get Compiz, but no luck.
I used [this]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") guide.
When I typ 'compiz --replace' in a terminal, i get this:
> kris2@kris-desktop:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Not initializing the Gtk-Qt theme engine

How can I get it working?

Thanks in advance

---

### Post by shafin on 2008-02-05
Whats you graphics card? Seems like it's driver is not authorized to be used in gutsy. I assume its intel X 3000,as you dont have xgl also. And again what version of kubuntu you were running? 7.10? KDE 3 or KDE 4?

---

### Post by shafin on 2008-02-05
In case you use an intel X 3000,try this
> 
[Source]("http://ubuntuforums.org/showpost.php?p=4222222&postcount=4")
1. type these and press enter:

[COLOR=SeaGreen]sudo gedit /usr/bin/compiz [/COLOR]

to open gedit and edit a file of compiz

2. find this:

[COLOR=seagreen]# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details 
T=" 1002:5954 1002:5854 1002:5955" # ati rs480 
T="$T 1002:4153" # ATI Rv350 
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965 
T="$T 8086:2972" # i965 (x3000) 
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T" [/COLOR]

and change all these lines into:

[COLOR=seagreen]# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T" 
BLACKLIST_PCIIDS="" [/COLOR]



---

### Post by Kris001 on 2008-02-05
Hi shafin,
My graphic card is a 'nVidia GeForce2 MX/MX 400'. I have Kubuntu 7.10, and I've installed KDE3, KDE4 and Gnome, but I use KDE3 the most ;)

Thanks in advance

---

### Post by Kris001 on 2008-02-06
Pleasy, anyone? :)

---

### Post by shafin on 2008-02-06
then this thread might interest you:
[http://ubuntuforums.org/showthread.php?t=468258](http://ubuntuforums.org/showthread.php?t=468258)

Also what driver you are using? You need to install the closed source nvidia driver in order to use compiz fusion,not the nv driver.

---

