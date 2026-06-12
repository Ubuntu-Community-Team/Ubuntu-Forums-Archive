---
title: "help with terminal navigating"
date: 2009-05-17
forum: General Help
---

### Post by s3nsiu on 2009-05-17
im trying to navigate my terminal to desktop where there is an run file i need to install
i m trying for an hour now but nothing
please dont tell me the common answers
cd /home/user/Desktop
cd /Desktop
cd ~/Desktop
etc they all show no such file or directory as a result
please help me im really mad.....im trying for hrs.
I have made a copy of the file on my Home folder. At least tell me how to navigate there
the Home folder on terminal.
im using ubuntu 8.04

---

### Post by nandemonai on 2009-05-17
> **s3nsiu said:**
> im trying to navigate my terminal to desktop where there is an run file i need to install
i m trying for an hour now but nothing
please dont tell me the common answers
cd /home/user/Desktop
cd /Desktop
cd ~/Desktop
etc they all show no such file or directory as a result
please help me im really mad.....im trying for hrs.
I have made a copy of the file on my Home folder. At least tell me how to navigate there
the Home folder on terminal.
im using ubuntu 8.04

That's odd..

Both:

```
cd
```
```
cd ~/
```

Will take you to your home directory. 

```
cd ~/Desktop 
```

should work fine.

Does Desktop show up in the list from a 

```
ls -l ~/
```

Something sounds fishy.

---

### Post by s3nsiu on 2009-05-17
dimitris@dimitris-laptop:~$ cd
dimitris@dimitris-laptop:~$ cd ~/Desktop
bash: cd: /home/dimitris/Desktop: No such file or directory
dimitris@dimitris-laptop:~$ 

no solution
same result
i stop trying .....

---

### Post by _Purple_ on 2009-05-17
Can you post the output of
```
ls /home/dimitris
```

---

### Post by s3nsiu on 2009-05-17
dimitris@dimitris-laptop:~$ ls /home/dimitris
ati-driver-installer-9-3-x86.x86_64.run      &#916;&#951;&#956;&#972;&#963;&#953;&#959;
Examples                                     &#904;&#947;&#947;&#961;&#945;&#966;&#945;
hybrid_wl                                    &#917;&#953;&#954;&#972;&#957;&#949;&#962;
wl                                           &#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
WLan Driver Broadcom 802.11g 3.100.46.0.zip  &#924;&#959;&#965;&#963;&#953;&#954;&#942;
&#914;&#943;&#957;&#964;&#949;&#959;                                       &#928;&#961;&#972;&#964;&#965;&#960;&#945;
dimitris@dimitris-laptop:~$

u can see the installer in my home folder. i copied there. its this file i want to run

---

### Post by nandemonai on 2009-05-17
Well.. you have no Desktop directory. Either that or it's in Greek which I can't read.

Are you using Gnome?

As for the installer.. it's a .zip. Are you sure it's a linux driver? Are you planning on using Windows drivers through ndiswrapper?

Regardless, you should be able uncompress the file with:

```
unzip WLan\ Driver\ Broadcom\ 802.11g\ 3.100.46.0.zip
```

---

### Post by s3nsiu on 2009-05-17
im a new in ubuntu. i cant understand the question. what is gnome

---

### Post by nandemonai on 2009-05-17
> **s3nsiu said:**
> im a new in ubuntu. i cant understand the question. what is gnome

The standard Ubuntu Desktop (window manager).

---

### Post by s3nsiu on 2009-05-17
> **nandemonai said:**
> The standard Ubuntu Desktop (window manager).
its the .run file i want to install. the ati driver.  not the zip. I should have deleted this cause it confuse u
as for gnome i dont think i have this

From ati help it says navigate to folder of .run file
and copy this command to terminal
sh ./ati-driver-installer-9.2-x86.x86_64.run 
but nothing...no result

---

### Post by nandemonai on 2009-05-17
> **s3nsiu said:**
> its the .run file i want to install. the ati driver.  not the zip. I should have deleted this cause it confuse u
as for gnome i dont think i have this

Oh right, my bad, I didn't notice that one.

Well this should work..

cd ~/

sudo ./ati-driver-installer-9-3-x86.x86_64.run

As for Gnome, if you haven't chosen Kubuntu and just installed Ubuntu and logged in as normal then you are using Gnome.

What I was getting at is that by default there should be a Desktop directory in your home directory.

I'm not sure if it's actually there but just in Greek because as I said, I can't read Greek ;)

---

### Post by s3nsiu on 2009-05-17
nandemonai ty for all but no result
cant navigate to desktop
run sudo ./ati-driver-installer-9-3-x86.x86_64.run
in the default directory and in home
but nothing
command not found is the message
leave it and ty for all.

---

