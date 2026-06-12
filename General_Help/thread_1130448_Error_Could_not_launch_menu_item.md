---
title: "Error Could not launch menu item"
date: 2009-04-19
forum: General Help
---

### Post by g35celicaz on 2009-04-19
I have ubuntu 8.10 and I just installed Wifi-radar on my laptop from Synaptic Package Manager. Now when I try to open Wifi-radar it has this error:

Could not launch menu item

Failed to execute child process "su-to-root" (No such file or directory)

Please Help 

 - Thanks

---

### Post by paradigm2 on 2009-04-19
> **g35celicaz said:**
> I have ubuntu 8.10 and I just installed Wifi-radar on my laptop from Synaptic Package Manager. Now when I try to open Wifi-radar it has this error:

Could not launch menu item

Failed to execute child process "su-to-root" (No such file or directory)

Please Help 

 - Thanks

It isn't able to find the program "su-to-root".

Go to a terminal and type

```

whereis su-to-root

```

and report the output.  This should tell us if it is installed and visible.

Here is what that program is:

[http://www.ambienteto.arti.beniculturali.it/cgi-bin/man2html?su-to-root+1](http://www.ambienteto.arti.beniculturali.it/cgi-bin/man2html?su-to-root+1) (a very old version of the man page)

---

### Post by g35celicaz on 2009-04-19
So I put this command in the terminal window:

whereis su-to-root

However it me this:

g35celicaz@g35celicaz-laptop:~$ whereis su-to-root
su-to-root:
g35celicaz@g35celicaz-laptop:~$ 

Now what do I do?

---

### Post by paradigm2 on 2009-04-19
> **g35celicaz said:**
> So I put this command in the terminal window:

whereis su-to-root

However it me this:

g35celicaz@g35celicaz-laptop:~$ whereis su-to-root
su-to-root:
g35celicaz@g35celicaz-laptop:~$ 

Now what do I do?

Hmm.  It appears that it has probably not been installed.

Maybe try:

```

sudo apt-get install su-to-root

```

What happens?  (it might be in another package, we'll see)

---

### Post by g35celicaz on 2009-04-19
Now I put this command in the terminal window:

sudo apt-get install su-to-root


And it gave me this:

g35celicaz@g35celicaz-laptop:~$ sudo apt-get install su-to-root
[sudo] password for g35celicaz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package su-to-root
g35celicaz@g35celicaz-laptop:~$ 

How can I fix this?


 - Thanks

---

### Post by paradigm2 on 2009-04-19
> **g35celicaz said:**
> Now I put this command in the terminal window:

sudo apt-get install su-to-root


And it gave me this:

g35celicaz@g35celicaz-laptop:~$ sudo apt-get install su-to-root
[sudo] password for g35celicaz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package su-to-root
g35celicaz@g35celicaz-laptop:~$ 

How can I fix this?


 - Thanks

Hold on a moment I will research it.  Unless someone else chimes in.  It appears there is a certain package you need to install.  I have it installed on my system.

Will try to get you what you need in a few minutes. :)

---

### Post by paradigm2 on 2009-04-19
Ok.

This should do it:

```

sudo apt-get install menu

```

Then try to launch your program again. :)

---

### Post by g35celicaz on 2009-04-19
Code: sudo apt-get install menu

Worked!

 - THANKS:D

---

### Post by mbkelly on 2009-05-16
> **paradigm2 said:**
> Ok.

This should do it:

```

sudo apt-get install menu

```Then try to launch your program again. :)

Thanks. That sorted me too :)

Mark

---

### Post by 3xp0r73m on 2010-07-30
Hey, i got ABSOLUTLEY the same problem, but when i type sudo apt-get install menu i got this:


```
elitza@elitza-laptop:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  menu
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 449kB of archives.
After this operation, 2,064kB of additional disk space will be used.
Err http://bg.archive.ubuntu.com/ubuntu/ lucid/universe menu 2.1.43ubuntu1
  Could not resolve 'bg.archive.ubuntu.com'
Failed to fetch http://bg.archive.ubuntu.com/ubuntu/pool/universe/m/menu/menu_2.1.43ubuntu1_i386.deb  Could not resolve 'bg.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
elitza@elitza-laptop:
```

Im trying to install WiFi Radar , becouse i cant connedt to my wifi router :(
And i think thats the only way :(
Thanks in advice!

---

