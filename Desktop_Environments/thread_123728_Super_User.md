---
title: "Super User"
date: 2006-01-30
forum: Desktop Environments
---

### Post by shade11 on 2006-01-30
I have this stupid RPM file that doesnt want to be converted via Alien. IT is VMware. I decided to use kPackage. But it askes me to type my ROOT password and it doesnt work. It says su authentication failure or something like that. SU meaning Super user I looked in Synaptic for something that would help, but nothing. Even if someone here can provide me with a .deb of VMware (PLEASE!) I will still have this problem becuase there are things I have come across that require Super User. Please Help.

---

### Post by RAOF on 2006-01-30
Anytime you need root/super user privileges, just run the command with "sudo".  In this case, you'd be after something like "sudo alien foo.rpm".  Or, in this case, "sudo kpackage foo.rpm", or whatever.

---

### Post by aysiu on 2006-01-30
If the vm packges is on your desktop, type these commands (assuming the name starts with the letters *vm*): ```
sudo apt-get update
sudo apt-get install alien
cd Desktop
sudo alien -i vm*.rpm
```

---

### Post by shade11 on 2006-01-31
No I cant. I tried alien already and it didn't work.

---

### Post by aysiu on 2006-01-31
Why not try [the .tar.gz version](http://download3.vmware.com/software/wkst/VMware-workstation-5.5.0-18463.tar.gz), then?

---

### Post by shade11 on 2006-02-01
I finally got the rpm converted into a deb. Now comes another problem . . . what do I do next? Nothing in the menu I tried typing vmware in the terminal and I don't know what to do next.

---

### Post by alamba on 2006-02-01
Are you installing vmware player or vmware workstation? 
Incase its player don't bother cos it wont work with alien. (Tried and failed). Download the tar package and it'll compile wonderfully and get u up and running in no time. 
Incase its workstation I have no experience of alient working or not.

A

---

### Post by shade11 on 2006-02-01
It is VMware player. Well, I will un-install it and then attempt to compile it from sorce code. But I really suck at that.

---

### Post by alamba on 2006-02-04
Me too. However this one worked without any glitches. Just need to make sure you have the header files and that you give the right path to it.

Akshay

---

### Post by shade11 on 2006-02-07
I don't know how to install the tar.gz package. It is too confusing. How do you install the .pl file in it. I did chmod +x and then "sudo"ed it. But no luck. It says that VMware was installed, but i removed it!!!

---

