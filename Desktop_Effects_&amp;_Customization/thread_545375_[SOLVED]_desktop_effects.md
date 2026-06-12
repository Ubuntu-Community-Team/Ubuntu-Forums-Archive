---
title: "[SOLVED] desktop effects"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by d_iane1954 on 2007-09-07
i have no desktop effects under system -preferance can someone please tell me how i would obtain it . thanks in advance am new to linux and would appreciate the help!!!!

---

### Post by Inxsible on 2007-09-07
you would have to install the desktop-effects package.

```
sudo aptitude install desktop-effect
```

Are you trying to get Compiz Fusion or regular Compiz ?

Compiz Fusion doesn't require desktop-effects and it is actually a good idea to remove it if you are trying to install Compiz Fusion.

---

### Post by d_iane1954 on 2007-09-07
> **Inxsible said:**
> you would have to install the desktop-effects package.

```
sudo aptitude install desktop-effect
```

Are you trying to get Compiz Fusion or regular Compiz ?

Compiz Fusion doesn't require desktop-effects and it is actually a good idea to remove it if you are trying to install Compiz Fusion.

not really sure have done nothing with linux as of yet downloaded and installed ubuntu studio 32 bit fiesty fawn and am perfectly new at this. just read a couple forms and i seen that this option was to be available.thanks for youe reply and help but im really trying to figure out what i do with this info you supplied me with.sorry for being so new and not understanding!!!

---

### Post by d_iane1954 on 2007-09-07
> **Inxsible said:**
> you would have to install the desktop-effects package.

```
sudo aptitude install desktop-effect
```

Are you trying to get Compiz Fusion or regular Compiz ?

Compiz Fusion doesn't require desktop-effects and it is actually a good idea to remove it if you are trying to install Compiz Fusion.

upon using this comand the folowing apeared:jerry@static24-89-92-164:~$ sudo aptitude install desktop-effect
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "desktop-effect".  However, the following
packages contain "desktop-effect" in their name:
  desktop-effects 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

any help and again thanks for your patience and understanding!!!!

---

### Post by Inxsible on 2007-09-07
> **d_iane1954 said:**
> not really sure have done nothing with linux as of yet downloaded and installed ubuntu studio 32 bit fiesty fawn and am perfectly new at this. just read a couple forms and i seen that this option was to be available.thanks for youe reply and help but im really trying to figure out what i do with this info you supplied me with.sorry for being so new and not understanding!!!If you are new to Linux and don't feel comfortable with the CLI, you can use the graphical method. Go to System --> Administration --> Synaptic Package Manager. IT will ask you for your root password. Supply that and once Synaptic opens, search for "desktop effects" without the quotes.

It will give you a bunch of packages related to desktop effects. you can then right click on the one you want and install.

Hope that helps !

---

### Post by Inxsible on 2007-09-07
> **d_iane1954 said:**
> upon using this comand the folowing apeared:jerry@static24-89-92-164:~$ sudo aptitude install desktop-effect
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "desktop-effect".  However, the following
packages contain "desktop-effect" in their name:
  desktop-effects 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

any help and again thanks for your patience and understanding!!!!
My bad, the package is probably named desktop-effects

---

### Post by d_iane1954 on 2007-09-07
thank you very much for your patient help,it sure is appreciated!!!!!!!!

---

### Post by Inxsible on 2007-09-07
> **d_iane1954 said:**
> thank you very much for your patient help,it sure is appreciated!!!!!!!!
you are welcome.

mark your thread as solved if your questions have been answered. Thread Tools --> Mark thread as solved.

---

