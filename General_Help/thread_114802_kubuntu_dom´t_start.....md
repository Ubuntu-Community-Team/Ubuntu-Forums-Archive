---
title: "kubuntu dom´t start...."
date: 2006-01-09
forum: General Help
---

### Post by tneto on 2006-01-09
HI

I install kubuntu in a  asus A6VA laptop... First i have a problem with the starting of hotplug service subsystem (the system dont boot), but i already resolve this ( i delete the file that start´s hotplug service).
Now my sytem boots ok but kde don´t start.... I think that is some problem with X...
The screen stays black and some times the computer restarts after some time...
This computer have an ati x700 mobility radeon.

Anyone can help me with this...??
Tks

---

### Post by ipn1nj4 on 2006-01-09
Instead of deleting the service, blacklist the bad modules in 

/etc/hotplug/blacklist

---

### Post by feathers on 2006-01-09
There is a bug in the ati driver. It is not solved in breezy yet. You could install the x-server from dapper. I did it and it worked.

---

### Post by tneto on 2006-01-10
Could you explain to me this procedure whith some detail please....or give me some information about this. 
I am a newbie.....;) 
Tks for the help!!
Best regars

---

### Post by feathers on 2006-01-10
In your /etc/sources.list: Exchange breezy for dapper (except where it says breezy-security, breezy-backports or so. It wouldn't do any harm but it is useless). Then type: sudo apt-get update. Without the full stop. This gets the new packet lists. I hope you have a fast internet connection. Then type: sudo apt-get install xserver-xorg-driver-ati. It should install the driver and all packages that have to be updated as well. I am not so very sure what it does because I used adept and just chose every xorg package. If this is not enough you must update the other xorg packages. Type: apt-cache search xorg | grep xorg. This shows you all xorg packages. You must then install them manually by typing: sudo apt-get install xorg-common xserver-xorg-core                    and so on, you get the idea. Hope this helps, if not, come back.

---

