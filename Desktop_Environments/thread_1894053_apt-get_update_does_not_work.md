---
title: "apt-get update does not work"
date: 2011-12-11
forum: Desktop Environments
---

### Post by smss on 2011-12-11
Hello.
I install a new ubuntu11.04-desktop-amd64 and now when i go to update the packages in terminal by this command : < sudo apt-get update > i faced with this error!!and not influence this command : <sudo dpkg --configure -a> !!!! please help me!
```
smss@smss-net:~$ sudo apt-get update
[sudo] password for smss: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
smss@smss-net:~$ sudo dpkg --configure -a
smss@smss-net:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
smss@smss-net:~$ 
```

---

### Post by NadirPoint on 2011-12-11
> **smss said:**
> Hello.
I install a new ubuntu11.04-desktop-amd64 
Why would you do that when 11.10 has been available for months?

I'd suggest starting over with the current release.

---

### Post by bluexrider on 2011-12-11
> **smss said:**
> Hello.
I install a new ubuntu11.04-desktop-amd64 and now when i go to update the packages in terminal by this command : < sudo apt-get update > i faced with this error!!and not influence this command : <sudo dpkg --configure -a> !!!! please help me!
```
smss@smss-net:~$ sudo apt-get update
[sudo] password for smss: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
smss@smss-net:~$ sudo dpkg --configure -a
smss@smss-net:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
smss@smss-net:~$ 
```

you have 2 instances of a apt-get open at the same time. using software manager and synaptic at the same time does not work.

---

### Post by smss on 2011-12-11
> **NadirPoint said:**
> Why would you do that when 11.10 has been available for months?

I'd suggest starting over with the current release.
i know,but i easier with this.

---

### Post by smss on 2011-12-11
> **bluexrider said:**
> you have 2 instances of a apt-get open at the same time. using software manager and synaptic at the same time does not work.
i know this matter.and i just opened one terminal !!!

---

### Post by smss on 2011-12-11
Did crashed my ubuntu?

---

### Post by smss on 2011-12-11
Oh! now worked apt-get update!!! How can this be?

---

### Post by BC59 on 2011-12-11
Try to run this in a terminal:

```
sudo rm /var/lib/dpkg/lock   
sudo dpkg --configure -a
```

---

### Post by smss on 2011-12-11
> **BC59 said:**
> Try to run this in a terminal:

```
sudo rm /var/lib/dpkg/lock   
sudo dpkg --configure -a
```
why remove it?

---

### Post by BC59 on 2011-12-11
The unblock the dpkg but if it's working it's all right.

---

### Post by bluexrider on 2011-12-11
> **smss said:**
> Oh! now worked apt-get update!!! How can this be?

if its working no need to remove lock. 

if you find its NOT working follow BC59 lead

---

