---
title: "installing softwares ?"
date: 2008-12-25
forum: General Help
---

### Post by BaderEX on 2008-12-25
Am new to ubuntu and I have a problem with installing new software 
 and my second question whats the different between 
amd64 and i386  in this link 
[http://packages.ubuntu.com/hardy/utils/unrar](http://packages.ubuntu.com/hardy/utils/unrar)

Thank you in advance :popcorn:

---

### Post by Moop on 2008-12-25
To install software it's best to use Applications-Add/Remove or System- Administration-Synaptic Package Manager.

I-386 is for the 32bit version of Ubuntu and AMD64 is for the 64bit version.

---

### Post by BaderEX on 2008-12-25
> **Moop said:**
> To install software it's best to use Applications-Add/Remove or System- Administration-Synaptic Package Manager.

I-386 is for the 32bit version of Ubuntu and AMD64 is for the 64bit version.

Thank you 

I tried to install 7-zip but i got this error 

[IMG]http://img135.imageshack.us/img135/2530/screenshotgnomeappinstahm1.png[/IMG]

And how do i do i know if my system is 32-bit or 64-bit


Marry Christmas :)

---

### Post by taurus on 2008-12-25
Applications -> Accessories -> Terminal
```
uname -m
```
i686 = 32bit
x86_64 = 64bit

Does your machine connect to the net?

---

### Post by BaderEX on 2008-12-25
> **taurus said:**
> Applications -> Accessories -> Terminal
```
uname -m
```
i686 = 32bit
x86_64 = 64bit

Does your machine connect to the net?


yes am typing this from this machine (ubuntu)

---

### Post by x1a4 on 2008-12-25
To get the list of packages hit the 'Reload' button.  

7zip is in packages **p7zip** & **p7zip-full**.  Just search for 7zip and you'll get all the 7-zip packages.

---

### Post by BaderEX on 2008-12-25
> **x1a4 said:**
> To get the list of packages hit the 'Reload' button.  

7zip is in packages **p7zip** & **p7zip-full**.  Just search for 7zip and you'll get all the 7-zip packages.

 I did but it doesn't check it and nothing will change, Am using DELL mini 9

---

### Post by BaderEX on 2008-12-26
Please any advice ?

---

### Post by Moop on 2008-12-26
Check your Software Sources. System-Administration-Software Sources. Main, Multiverse and Universe should be checked (enabled) and cd-rom should be unchecked.  Then try reloading.

---

### Post by BaderEX on 2008-12-26
> **Moop said:**
> Check your Software Sources. System-Administration-Software Sources. Main, Multiverse and Universe should be checked (enabled) and cd-rom should be unchecked.  Then try reloading.


I did that and got this error 

[IMG]http://img234.imageshack.us/img234/9136/screenshotom0.png[/IMG]

whats going on ?

---

### Post by taurus on 2008-12-26
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by BaderEX on 2008-12-26
> **taurus said:**
> Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```


```


# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy main universe multiverse




```

---

### Post by taurus on 2008-12-26
What's all you have, one repo in /etc/apt/sources.list?

Aren't you using Dell mini?

---

### Post by BaderEX on 2008-12-27
> **taurus said:**
> What's all you have, one repo in /etc/apt/sources.list?

Aren't you using Dell mini?

Yes am using DELL mini 9 and All i have in etc/apt/source.list is in the previous reply

---

### Post by Moop on 2008-12-27
Your sources are all commented out. You need to remove the # from in front of the lines to enable them. Example:

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
```In a terminal ```
sudo gedit /etc/apt/sources.list
```  Make the changes then save and exit. Now in terminal run ```
sudo apt-get update

```

---

### Post by BaderEX on 2008-12-28
Moop,

Thanks man I did work like a charm :)

Happy new year! :)

---

### Post by nkmcquain on 2009-09-08
whats the name of your internet browser?  i use firefox and it wont play audio from youtube etc.

---

