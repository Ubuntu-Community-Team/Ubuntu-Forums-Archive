---
title: "nVidia Driver issue"
date: 2006-06-04
forum: Desktop Environments
---

### Post by chetanthaker on 2006-06-04
Hey guys, 

I'm still learning how to use KUbuntu and this nVidia thing has driven me NUTS all the time -- 

Ok, here goes

I had Breezy and yesterday I upgraded to Dapper from the CD -- this went well

Then I installed 'nvidia-glx' and that too got installed fine

After that, whenever I tried running X-server, I would get that stupid MWM Pager thingy, for which, I had to quit X -- I found out that GLibCore or something was creating an issue with X

So I opened my xorg.conf and changed the driver to 'vesa' and started X -- 
X loaded, but then I have had this login splash that was creating errors (since   the time I had Breezy) - it said "cannot find the login splash at /some/place/in/my/PC' and gives me the default login screen, wherein I put the username and password, and the login splash error comes up again and asks me to put in my username and password (infinite loop)


So how do I get my X back ??
I'm sending you 2 of my xorg.confs -- one is xorg.nvidia (when the libcore error comes up and does not start X) and the other one is the default one (wherein I've changed it to vesa)

Please do help guys !!


CeeTee

---

### Post by tseliot on 2006-06-04
Try this:
[http://www.ubuntuforums.org/showthread.php?t=187177&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=187177&highlight=nvidia")

---

### Post by chetanthaker on 2006-06-04
Naah, still having a problem

Herez my Xorg log file


CeeTee

---

### Post by tseliot on 2006-06-04
Try this:
```
sudo dpkg --configure -a
```

Then
Reconfigure the Xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

and select the "**vesa**" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

And tell me if it works. Only then we can try installing the nvidia driver.

---

### Post by chetanthaker on 2006-06-04
Dude when I try to reconfigure xserver-xorg, it says KDM is bad or something

I try saying "sudo apt-get install kubuntu-desktop" and it wont let me let me install it coz some package is missing or not 
installable
and then I try

sudo apt-get -f install 
and there is one package kde-crystal-something cannot be installed

Im kinda stuck !

---

### Post by chetanthaker on 2006-06-04
Hey dude, I followed your instructions and my box is back up 
Thanx a lot pal :)

God Bless

---

