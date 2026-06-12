---
title: "it takes 3 minutes to boot (X)ubuntu"
date: 2005-08-08
forum: Desktop Environments
---

### Post by ferenkileen on 2005-08-08
because of an old pc (celeron 500 128mb ram 8gb HD) i decided to make a  server installation of ubuntu plus the xfce4 WM (obiowsly following the useful howto founded here)

Xfce is quite responsive (obiowsly firefox is slow but)
the problem is that it takes too much time to boot the system (more or less 3 minutes!! its unbereable....)
I need some tips to set it faster.....
I've already: 
- chmod -x some unnecessary services
- removed gdm and set login with a script found here
- installed a very minimal system 
- I'm running a memory test (to see if something's broken)

I need tips -- suggestions ---hhheeeelp! :-)
Dont let me throw away that old jewel....

---

### Post by eivind on 2005-08-08
Quick tip: Sometimes, network interfaces take terribly long to bring up. At least, that's a common complaint with ubuntu bootup.
By the way: Are you absolutely sure that chmod -x on services prevents them from starting? Doesn't it just cause the startup scripts to look for the executables which you have made non-executable? 
It would perhaps be better to use init script editors to stop services upon boot. Examples are sysv-rc-conf or sysvconfig (sudo apt-get install any of them). I have used sysv-rc-conf with success.


Cheers,

Eivind

---

### Post by Curlydave on 2005-08-08
Ubuntu always took significantly longer to boot than Windows for me, but 3 mins is over the top.

---

### Post by Lord Illidan on 2005-08-08
Can u install some more RAM. My old Celeron 333 mhz had 196 mb of ram and was quite "fast"..

An extra stick of...say 64 mb, will help a lot in improving performance...

---

### Post by ferenkileen on 2005-08-08
- cant find ram compatible with my pc
- networking stuff are the only one that are faster :-) 
- i'll give a try to sysv-rc-conf 

I'll tell you....

---

### Post by kostkon on 2005-08-08
My normal Ubuntu installation on my Pentium MMX 200MHz, 128MB RAM takes about the same time (~3 mins) but I don't say much... cause after that I have an equivalent-better OS, compared to WinXP, running at a decent speed. And, as you all know, WinXP would not even start to boot on that type of PC...!!

Thus, ferenkileen, think what you gain using Ubuntu and if you think of it, it's just the boot, no big deal: you are using the PC as a server, you don't need to (re)boot often.

The 3 mins is nothing compared to what you get after the boot on such a deprecated PC.

EDIT: I realised that you don't necessarily use this PC as a server, you just did the server installation to use XFCE instead of Gnome. OK, I got it! Even with that, my point is valid and in my opinion the 3 mins booting is OK even if you open-close your PC often.

---

### Post by ferenkileen on 2005-08-08
you misunderstood....
I did a server installation (only base pkg installed in order to put a lighweight WM)

i know that i'd be happy bout it but I know that I can change things....
probably i'ts something concerned with the initrd kernel that loads not enogh memory.....

if it takes 3 minutes (on every machine --even the slower -- means that something's gone wrong.....) I'm not complaining with the graphical apps.... 
think about it....probably u have some problems too... :-)

---

### Post by coolclassic on 2005-08-08
Try removing some services at start time:

Apache
mysql
network
modem

and increas your ram very very very cheep from ebay.

---

### Post by TestDummy! on 2005-08-15
[QUOTE=ferenkileen]- cant find ram compatible with my pc
- networking stuff are the only one that are faster :-) 
- i'll give a try to sysv-rc-conf 

I'll tell you....[/QUOTE]

Nobody carries a stick of PC66 SDRAM anymore? 

What about checking at a little mom-and-pop kinda computer shop for that stuff, not like a giant electronics store.  :neutral: 

Besides, 64MB PC66 woudn't be that much, I paid like $20 for 128MB PC66 a few years ago.

---

### Post by joker on 2005-09-01
I have a 400 mhz celeron with 256 meg of ram loaded with ubuntu, default install, although I loaded XFCE4 and usually boot into that as it is 11 seconds from login screen to usable desktop as opposed to 30ish seconds from login to gnome.  But power on to login screen is only 1min 40 seconds, I am booted into XFCE4 in under 2 minutes from power on with a machine 100mhz slower than yours.  

FYI, PC100 and PC133 will often work in place of PC66 as long as it is a 128mb stick or smaller.  You would be suprised how many people have old PCs sitting in the attic or closet just waiting to be picked over for parts, I suggest asking your friends and relitives if they have anything they would like to donate to you, I have had 4 PCs donated to me like this... of course it helps that I do all my familys tech support I suppose.  Oh, always ask the woman of the house, they are more likely to want the junk gone.

---

### Post by Galoot on 2005-09-01
There's always a bright side. It's not Windows, so you won't need to reboot often.

</not helpful>

---

### Post by mlomker on 2005-09-01
[QUOTE=Galoot]There's always a bright side. It's not Windows, so you won't need to reboot often.

</not helpful>[/QUOTE]
 It would have helped if he'd given us some details on where it pauses.  I get a pause while the kernel looks at the BIOS and if a network card is unplugged you'll get a *really* long pause while the system tries to find a server to set its time to.  If it's pausing somewhere else then maybe something's wrong.

You could also try compiling a smaller kernel...though that can be time consuming business until you get it just right.  Tweaking the startup services is a good call...email servers and other things are loading in there.

---

