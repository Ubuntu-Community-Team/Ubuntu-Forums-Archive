---
title: "Debian Problems"
date: 2008-04-15
forum: Debian
---

### Post by kevCast on 2008-04-15
Hello, I recently installed Debian on a notebook of mine. A few problems though; the clock is wrong, even though it's set to my timezone, it's five hours off. Also, how do I get my Broadcom 4306 card working in Debian? I've become accustomed to the Ubuntu way with the Restricted Driver Manager; how do I really do it? When I try to install bcm43xx-fwcutter, it falls to install. Any advice? Also, I'd like to be able to get torrents to work, but it my system won't allow it. Any ideas on how to fix this without the help of a GUI?

Any and all help is appreciated, thank you.

---

### Post by kerry_s on 2008-04-15
that's start with the clock->
in terminal:
su
apt-get install ntpdate

i'm guessing the wireless is probably in a different repo, make sure you add "contrib non-free" here's mine, you can add the lenny but leave the #, you need to be fully up to date in etch first before turning on lenny repo's and you have to do it 1 repo at a time else you'll get a error about to many repos.->
```

deb http://ftp.debian.org/debian/ etch main contrib non-free  
#deb http://ftp.debian.org/debian/ lenny main contrib non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
#deb http://security.debian.org/ lenny/updates main contrib non-free 

deb http://www.debian-multimedia.org/ etch main 
#deb http://www.debian-multimedia.org/ lenny main 

```

then run> **apt-get update**
then get yourself a gui> **apt-get install synaptic**

i don't understand about the torrents, what won't allow?

---

### Post by kevCast on 2008-04-15
non-free and contrib are both enabled. When I try to install bcm43xx-fwcutter though, it gives me a dpkg error for bcm43xx-fwcutter. When I run dpkg --configure bcm43xx-fwcutter, it gives me the same error.

I don't need Synaptic, nor can i run it. P3 and 64MB ram makes it too much of a burden. I just use apt-cache search *blank* when I need to find something.

---

### Post by kerry_s on 2008-04-15
> **kevCast said:**
> non-free and contrib are both enabled. When I try to install bcm43xx-fwcutter though, it gives me a dpkg error for bcm43xx-fwcutter. When I run dpkg --configure bcm43xx-fwcutter, it gives me the same error.

I don't need Synaptic, nor can i run it. P3 and 64MB ram makes it too much of a burden. I just use apt-cache search *blank* when I need to find something.

okay, you got to be more specific about the error.
try> apt-get -f install

yeah synaptic would be a bit heavy, aptitude should be installed by default, it's like synaptic for the console, just takes getting use to.
su
type> aptitude

i know what you mean, i use the console on mine, but i have alias's setup.

---

### Post by kevCast on 2008-04-16
I found out what was wrong with my wirless; I didn't have bzip2 installed. :P I jumped from Etch to Lenny, and installed the b43-fwcutter. I have the firmware installed from it, but I don't know where to go from there. Also, my Xorg is making my cursors weird. I have an example in the screenshot below.

---

### Post by kerry_s on 2008-04-16
> **kevCast said:**
> I found out what was wrong with my wirless; I didn't have bzip2 installed. :P I jumped from Etch to Lenny, and installed the b43-fwcutter. I have the firmware installed from it, but I don't know where to go from there. Also, my Xorg is making my cursors weird. I have an example in the screenshot below.

well you said you liked the network manager, search network-manager
or just google, i'm sure there are lighter alternative to control wireless.

cursor, you mean the terminal?

---

### Post by doorknob60 on 2008-04-19
Wicd is a good alternative to network-manager. It's pretty lightweight and doesn't require gnome. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

> Installing Wicd in Debian

You can also use the apt repository. Just add the following line to your /etc/apt/sources.list 
deb [http://apt.wicd.net](http://apt.wicd.net) debian extras 
Now you can apt-get update and apt-get install wicd to install wicd.

---

