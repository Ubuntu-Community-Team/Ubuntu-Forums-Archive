---
title: "help upate error"
date: 2009-03-03
forum: General Help
---

### Post by Shaddon on 2009-03-03
i was installing flash and when i restarted it said i had updates tryed to run it i get dpkg and i followed and still have the problem

---

### Post by taurus on 2009-03-03
What happens when you run these two commands from a terminal?  Make sure you close update manager first.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Shaddon on 2009-03-03
so i tryed that and i got 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Sources
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [81.3kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [3491B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [22.7kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [1154B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [29.3kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [5440B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [6406B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [1860B]
Fetched 196kB in 4s (40.4kB/s)                  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by taurus on 2009-03-03
Do you have update manager, add/remove, or synaptic open right now?  You must close it before you run those two commands from a terminal.

---

### Post by Shaddon on 2009-03-03
the update is on my top tool bar saying theres updates ready. im not sure about how to turn that off

---

### Post by taurus on 2009-03-03
You can click the right button of your mouse on the icon and cancel it.

---

### Post by Shaddon on 2009-03-03
i tryed the right click and it does not have cancelle option, but i tryed unchecking all of them to see if that would work it hasn't anyother option

---

### Post by Shaddon on 2009-03-03
i tryed a system restart to cancelle what ever was running at the time and tryed the sudo upate command and this is what it said
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by taurus on 2009-03-03
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Shaddon on 2009-03-03
thx bro, that worked for me
by chance do you now where there is a list of codes for the terminal

---

