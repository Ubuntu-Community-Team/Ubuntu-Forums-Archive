---
title: "another desktop wont get enabled"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by SuperXero on 2007-10-20
i have an ati x1600 mobile radeon and i installed the driver but wheni go to the restricted drivers manager it still wont let me enable it

---

### Post by Ub1476 on 2007-10-20
There's a driver in there, right?

Okay, open terminal then do:

```
sudo apt-get update
sudo apt-get upgrade
```

Try to enable now.

Edit: What do you mean by "installed driver" then "wont let me enable in RDM"? If it's installed (and is the correct one) you don't need to use the one in RDM.

---

### Post by SuperXero on 2007-10-20
ok i did that and this is what i got 

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Fetched 1B in 0s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



i have no idea what that means >_<

---

### Post by SuperXero on 2007-10-20
also when i go to the restricted drivers is ayas that another synaptic is running in interactive mode

---

### Post by amadeus266 on 2007-10-20
You can't use more than one installer program at a time. RDM, Synaptec, Software Manager can't run when another is already running.

---

### Post by Ub1476 on 2007-10-20
Oh:lolflag:

You are probably running Synaptic already (Add/remove maybe?). Shut it down or just reboot your system so everything "Synaptic" related shuts down. Try the same again after that.

---

### Post by SuperXero on 2007-10-20
ic ic 

well now that i did that it said that nothing updated/upgraded but when i go to inable the ATI driver it now says that the package is broken

---

### Post by SuperXero on 2007-10-20
imma complete n00b at this the only thing i know how to do is set up a samba server in FC5 heh -__-;;

---

