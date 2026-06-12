---
title: "Starting up problem/freeze"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Terracotta on 2005-04-09
Hye, 
I've tried to install Kubuntu twice, with always another version of Kubuntu, I've tried to use the livecd, but the result is al the same, I get a greyish screen when starting kdm, the system doesn't get to the log in screen. I don't have a command line, and the system doesn't seem to respond to the keyboard, I can move the mouse though, but I can't do anything usefull with it.
Any help would be appreciated.
PS, I have a Geforce 6800, and an amd64 processor, so naturally I downloaded the x86_64 iso.

---

### Post by tiiim on 2005-04-09
[QUOTE=Terracotta]Hye, 
I've tried to install Kubuntu twice, with always another version of Kubuntu, I've tried to use the livecd, but the result is al the same, I get a greyish screen when starting kdm, the system doesn't get to the log in screen. I don't have a command line, and the system doesn't seem to respond to the keyboard, I can move the mouse though, but I can't do anything usefull with it.
Any help would be appreciated.
PS, I have a Geforce 6800, and an amd64 processor, so naturally I downloaded the x86_64 iso.[/QUOTE]
 i got a similar prob but with i386 and radeon x600 it freezes when kde gets to login. but mine is on the live cd and a bit hmmm to try the install cd!

---

### Post by macdo on 2005-04-09
Ah. I am not alone...
I decided to install kubuntu on both a laptop and a desktop at the same time - no problemo with the laptop, but a beautiful rainbow coloured screen on the desktop - only the mouse cursor appears to work!
It doesn't matter whether you install ubuntu or kubuntu, either, btw - I tried both!
If anybody has any ideas, I'd be very grateful!

cheers
macdo

--
If Microsoft made toasters, you'd need to reinforce your countertop to take the weight.
If Cray made toasters, they'd be the fastest in the world, but cost $30,000,000 each.

---

### Post by Terracotta on 2005-04-10
Oh btw, apparently someone posted the same problem and he thought it might be because he has mepis installed (he had installed it on a windows xp machine too and besides a konqueror bug it worked fine), just to tell you, I have mepis installed too, at the moment since it is the only distribution at the moment that seems to work :-s, would love to try kubuntu though since that one has an iso compiled for x86_64 and mepis just for i386, and Kubuntu has kde 3.4 of course wich I would love to try  :twisted:, oh and just to tell you, livecd or install cd, tried them both but they both give the same result ](*,)


Edit:
I used the preview and release candidate version, can anyone tell me if this problem was solved installing the official release?

---

### Post by macdo on 2005-04-13
nope, AFAIK the problem exists on the official release as well... :-(

cheers,

--
Macdo

Never forget that euh, hmm, ....

---

### Post by Terracotta on 2005-04-16
I just noticed it ;-), thanks for the info anyway.

Does anyone know if there's gonna be a bug fig release, since I really would like to start  using kubuntu? ](*,)

---

### Post by Terracotta on 2005-04-18
I think it's x86_64 xorg problem, I tried to install suse 9.2 64bit version and it gave the same result as kubuntu, whereas suse 9.1 64bit version didn't give any problem at all. Could anyone explain how to install xorg from the commandline, and/or to make kubuntu start without starting up kdm? or xorg?
Thanks.

---

### Post by Terracotta on 2005-04-24
Is there really no one, who knows how to solve this? ](*,) 
I would really like to try kubuntu  :---)

---

### Post by macdo on 2005-04-24
This is getting wierder and wierder - Debian (a close cousin to say the least!) installs fine... well, except for the ATI drivers, which are known to be buggy.

It's a real pain - I now have a laptop with Kubuntu, and a Desktop without...
 :evil:

---

### Post by Marshall1 on 2005-06-03
I've had the same problem using MEPIS.  The last working release was SimplyMEPIS 2004.02,  September 2004.  I'm still using it but now cruising other Debian distros.  

Graphics card is S3 Savage 4 32MB, an old one.  

For me, the problem is somehow related to the xdrvr=vesa boot option.  If I use that, I get the screen freezes with KDE programs (some but not all).  If I don't, the machine refuses to shut down when asked.

---

### Post by Futal on 2005-07-02
I have a problem which looks similar. I first tried Kubuntu on a AMD Mobile laptop with a Intel graphic chipset integrated to the motherboard, it worked fine and it looks so good I installed it on my own laptop: Pentium M with GeForce FX 5200 Go. It works fine. 

Now, I have just installed it on my mother computer, a desktop with Athlon 2600+ and a GeForce FX 5700, and the system freezes after a while when browsing the Internet with Konqueror. 

After a few hours of thinking, I found what may be the reason: I am using a xorg.conf file with DRI options commented but they are not by default, i.e. on the desktop (proprietary driver is installed on both computers with nVidia cards).

I will try with a modified xorg.conf and report it here if it works for me.

---

### Post by Futal on 2005-07-02
Well, it tooks me less than 5 minutes to see it is not the solution. :-(

Unfortunately, because of this and another critical bug (at least for my mum: a click on a KAddressBook email entry does not fill the message field "To:") I may have to install Mandriva back.

---

### Post by Hokputooy on 2005-07-05
For me in kdm the keyboard stops responding if i get the wrong password

---

### Post by davidm on 2005-08-05
It's sad to see so many iterations of the problem with no suggestions about a cure, but I have a datapoint to add to the former, and hope for the latter.

I installed Kubuntu 5.4 on two identical VIA boxes with Nehemiah processors and 1 GB of RAM. About four weeks after the install, on one of the boxes the keyboard stops responding after KDM processes the password. The date of the file xorg.conf in /etc/X11 shows it hasn't changed since the install, and booting the Kubuntu live CD works just fine.

Thanks to all the developers and users who make this engine run.

David Mitchell

---

