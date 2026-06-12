---
title: "&lt;---= noob please HELP wireless"
date: 2009-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by [WaZ]Pac-Man on 2009-02-19
Hello guys i literally have just started using Ubuntu today and ive installed it on my XpS M1710 and my wireless card is not working

its a dell 1500 ive searched through the forums and i see all theese commands and i have absolutely no idea what they are doing or talking about

im not a programmer so most of this stuff is like russian to me

if anyone would be willing to walk me through getting the damn thing to work please respond and id be very greatfull


thanks!!

-[WaZ]Pac-Man

---

### Post by anjilslaire on 2009-02-19
first thing to try, is plug the laptop into a wired connection so you have network access, then check the Hardware Drivers for an applicable driver:

System > Administration > Hardware Drivers

If the  system offers proprietary drivers, accept them or enable them as appropriate.

also, be sure to update your repositories to make sure you can get the latest software:

Applications > Accessories > Terminal, then type:
```

sudo apt-get update
sudo apt-get upgrade

```

install everything it offers, and see what  works afterwards, to start.

---

### Post by stopie on 2009-02-20
> **anjilslaire said:**
> also, be sure to update your repositories to make sure you can get the latest software:

Applications > Accessories > Terminal, then type:
```

sudo apt-get update
sudo apt-get upgrade

```install everything it offers, and see what  works afterwards, to start.

That worked for me with my gateway after I spent an hour trying to get the bcom 43xx to work with all of those repackaging guides - Id recommend update/upgrade as one of the first steps as well.

---

### Post by [WaZ]Pac-Man on 2009-03-01
> **anjilslaire said:**
> first thing to try, is plug the laptop into a wired connection so you have network access, then check the Hardware Drivers for an applicable driver:

System > Administration > Hardware Drivers

If the  system offers proprietary drivers, accept them or enable them as appropriate.

also, be sure to update your repositories to make sure you can get the latest software:

Applications > Accessories > Terminal, then type:
```

sudo apt-get update
sudo apt-get upgrade

```

install everything it offers, and see what  works afterwards, to start.

the thing is i dont want to update i like the version om running i just need to get the card to work

also sorry i didnt respond earlier ive been in the hospital all week

thanks for the help!

---

### Post by sirebral on 2009-03-01
You are not updating to a new version, you are just installing the updates for the version you are using.

Well, You **SHOULD** be.  What version are you using?

---

### Post by Transien on 2009-03-01
Use this to upgrade and install programs for your current distro: 
```

sudo apt-get update
sudo apt-get upgrade
```

Use this to upgrade your distro itself

```
sudo apt-get dist-upgrade
```

See the difference? You should be fine. Anyone second that?

---

### Post by [WaZ]Pac-Man on 2009-03-01
> **sirebral said:**
> You are not updating to a new version, you are just installing the updates for the version you are using.

Well, You **SHOULD** be.  What version are you using?

> **Transien said:**
> Use this to upgrade and install programs for your current distro: 
```

sudo apt-get update
sudo apt-get upgrade
```

Use this to upgrade your distro itself

```
sudo apt-get dist-upgrade
```

See the difference? You should be fine. Anyone second that?


im running gibbon 7.10 and yes i do see the difference

thanks!

---

### Post by [WaZ]Pac-Man on 2009-03-01
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


is what happens when i do that 
i'll restart it now and see if anything happens



NOTHING HAPPENED   still no wireless

---

### Post by sirebral on 2009-03-01
Here are some suggestions:

Go here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

and see if they have anything that might help.  From that page I would recommend downloading the DELL branded version of 7.10 and try updating from the CD you made.  Since it is a new install you might also attempt to install from the DELL branded 7.10.  

I also noticed they have 8.10 versions and 8.04 versions if you are interested in having a DELL branded Linux port.

---

### Post by [WaZ]Pac-Man on 2009-03-01
> **sirebral said:**
> Here are some suggestions:

Go here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

and see if they have anything that might help.  From that page I would recommend downloading the DELL branded version of 7.10 and try updating from the CD you made.  Since it is a new install you might also attempt to install from the DELL branded 7.10.  

I also noticed they have 8.10 versions and 8.04 versions if you are interested in having a DELL branded Linux port.

i found this page
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)
doesnt work as i have 7.10 not 7.04

so still nothing

---

### Post by Transien on 2009-03-01
I found a post in the Ubuntu forums that might help, but it is long and a little complicated. I'm not experienced enough in tweaking a system to tell you if it will work, but perhaps this will lead someone else on the right track. [[COLOR="Blue"]Here[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-628903.html") is the link.

It is a short thread, and it links to another Ubuntu forums post. The two together just might do the trick. [[COLOR="Blue"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=297092") is the link to the other post.

Good luck, and ganbatte!  :KS

---

