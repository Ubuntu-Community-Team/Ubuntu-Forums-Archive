---
title: "open source ati driver"
date: 2009-05-26
forum: General Help
---

### Post by tommah04 on 2009-05-26
hey all,

tried installing an open source ati driver as shown here...

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but it doesn't seem to be working and I don't know how to undo the changes... I'm at the command login and can't seem to really do anything....

any help?

---

### Post by tommah04 on 2009-05-26
sorry for the double post...

but I did eventually get it working, but everytime I start the computer I get an error saying I have to run on low-graphics, and that display:0 is busy so I have to switch to display:1

and I also can't use compiz fusion now.....

sooooo, if someone can either tell me how to get that all straightened out OR tell me how to undo everything I just did I'd be super happy.

thanks!

---

### Post by clhsharky on 2009-05-26
What release and ATI chip are you using?

---

### Post by tommah04 on 2009-05-26
is this what you're looking for?

Jaunty

tom@tom-desktop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV505 [Radeon X1550 Series] [1002:7143]

---

### Post by tommah04 on 2009-05-27
I undid everything and changed xorg.conf back to default..... so at least I can have compiz make my desktop look sexy.... but I really wish I would've been able to get my card working.....maybe I'll just switch to nvidia

---

### Post by gradinaruvasile on 2009-05-27
type
sudo dpkg-reconfigure -phigh xserver-xorg
at the command line.
reboot

The X server will be reconfigured including video drivers, display etc. 
The ati (in fact radeon) opensource driver is installed anyway by default for that card, no need to explicitly mention the driver in xorg.conf. Look at the /var/log/Xorg.0.log file after rebooting, you should see lots of RADEON lines there.

---

### Post by Legace on 2009-05-27
> **tommah04 said:**
> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV505 [Radeon X1550 Series] [1002:7143]

The FGLRX drivers for Jaunty do not support cards before 2XXX..
The open source drivers should be more than enough for you :)

---

### Post by tommah04 on 2009-05-27
kinda half off-topic question..... do most nvidia cards work with jaunty?
 
in other words, should I be worried about which one I'm buying or are the odds that it'll work quite high?

---

### Post by gradinaruvasile on 2009-05-28
> **tommah04 said:**
> kinda half off-topic question..... do most nvidia cards work with jaunty?
 
in other words, should I be worried about which one I'm buying or are the odds that it'll work quite high?

Yes they work. The Nvidia drivers are really good as far as i experienced it (i have a nvidia 7600 gs at home and quadro nvs 285 at work (dual monitors), quadro nvs 135 (i think) on my work laptop, geforce mx440 on my parents computer, all of them work perfectly with ubuntu 7.10-8.04-8.10-9.04 using the proprietary nvidia drivers). I might mention i use the nvidia provided drivers not the ubuntu ones (except for the mx440).
On the other hand we have 2 ati cards (x1300 and x1600) in our department  on ubuntu 9.04 - the open source radeon drivers are lagging behind in capabilities (some 3d stuff like glsl wont work at all) although they seem quite stable, the fglrx drivers we were using on ubuntu 8.10 seemed to be buggy (compared to the nvidia proprietary drivers). Cant speak for the 9.5 catalyst and latest Ati cards.
I think Nvidia is a safe bet if u ask me.

---

### Post by tommah04 on 2009-05-28
sweet, thanks

---

### Post by NormanFLinux on 2009-08-03
You have to edit your xorg.conf file to have Ubuntu acknowledge the open source ATI driver. The default vesa driver does not run compiz so the Ubuntu has to be told the correct driver to run: ATI.

Hope this helps.

---

