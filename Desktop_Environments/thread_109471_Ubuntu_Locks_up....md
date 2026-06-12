---
title: "Ubuntu Locks up..."
date: 2005-12-28
forum: Desktop Environments
---

### Post by DarkDancer on 2005-12-28
Ok, I was having problems with getting my wg311v3 card working, well, after I reloaded Ubuntu, I got ndiswrapper up and going, and then got the driver loaded from Windows. Called Sudo modprobe ndiswrapper to install the needed module. then did sudo ndiswrapper -m so that it would load at startup. The card is now seen and I can put in the WEP key, but if I say ok to the network management screen, Ubuntu locks up, oh yeah, and when I reboot, I have to load the module in again (though if I do the sudo ndiswrapper -m again, it says it's already loaded in the kernal). Any ideas?

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=DarkDancer]Ok, I was having problems with getting my wg311v3 card working, well, after I reloaded Ubuntu, I got ndiswrapper up and going, and then got the driver loaded from Windows. Called Sudo modprobe ndiswrapper to install the needed module. then did sudo ndiswrapper -m so that it would load at startup. The card is now seen and I can put in the WEP key, but if I say ok to the network management screen, Ubuntu locks up, oh yeah, and when I reboot, I have to load the module in again (though if I do the sudo ndiswrapper -m again, it says it's already loaded in the kernal). Any ideas?[/QUOTE]
Can you configure the WEP key from the terminal?  I think you can use "iwconfig" to do that.

Is it just the desktop that locks up, or can you get to a virtual terminal?  Does CTRL+ALT+Backspace work?

---

### Post by DarkDancer on 2005-12-28
It locks up tight as a drum, no mouse curser movement or anything....hmm, ctrl-alt-backspace, didn't know about that one, will try it. Thanks.

---

### Post by Dr. Nick on 2005-12-28
add **ndiswrapper **to /etc/modules for boot time loading.

Did you use your system before ndiswrapper? If so did it lock up aswell. I use ndiswrapper and my system locks at random with the 686 kernel but not the 386, not sure why this is.

Edit **/etc/network/interfaces** to add your wep key manually, Is using the wep gui the only time it locks up ?

---

### Post by DarkDancer on 2005-12-28
Hmmm, well, I wouldn;t say use, because I was mostly trying to get Ubuntu to work. I had to reload it to get ndiswrapper going (mainly because of some errors of my own), but once I reloaded, and retried ndiswrapper, it worked and the card became visible. then when I go into the network setup, and set up the card (including the wep) then activate it and try to close network set up, it freezes...

I'll try putting the key in that file.....not sure if I know how to do it, but we'll see.

---

### Post by Dr. Nick on 2005-12-28
[quote=DarkDancer]Hmmm, well, I wouldn;t say use, because I was mostly trying to get Ubuntu to work. I had to reload it to get ndiswrapper going (mainly because of some errors of my own), but once I reloaded, and retried ndiswrapper, it worked and the card became visible. then when I go into the network setup, and set up the card (including the wep) then activate it and try to close network set up, it freezes...

I'll try putting the key in that file.....not sure if I know how to do it, but we'll see.[/quote]

to add it should be as easy as putting this line in
```
wireless-key xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
```
replacing the x's with the hex values of your wep which can be obtained from the router.

If you have other computers on the lan you may login to the router and disable wep to make sure you can connect from ubuntu

---

### Post by DarkDancer on 2005-12-28
Thanks, 'cause I would have never gotten that...

---

### Post by DarkDancer on 2005-12-28
modules and interfaces are both read only files and I have no idea how to remedy that.......

---

### Post by Dr. Nick on 2005-12-28
ah thats true, use sudo to open them

eg. sudo gedit /etc/network/interfaces
and sudo gedit /etc/modules 
from a terminal

---

### Post by DarkDancer on 2005-12-28
Thanks! I'll try that tomorrow... ;)

---

### Post by DarkDancer on 2005-12-29
Ok Dr. Nick, I triued your suggestions and here's what happened. I edited interfaces and modules to put in the wep key and the wep key and ndiswrapper respectively. ndiswrapper now loads on boot, however the wep key does not. Could it be because I can not acticvate the card? after activation, when I try to leave the network screen is when Ubuntu locks up, so it never seems to take the activation......I'm lost....

---

### Post by DarkDancer on 2005-12-30
Ok, I got it, I am posting this from Ubuntu now, not sure how I did it exactly, and am afraind to reboot, hehe, but it shouldn't be a problem..... ;)

---

### Post by Dr. Nick on 2005-12-30
[quote=DarkDancer]Ok, I got it, I am posting this from Ubuntu now, not sure how I did it exactly, and am afraind to reboot, hehe, but it shouldn't be a problem..... ;)[/quote]

Heh
If you need to activate it from the command line sometimes the command 
**sudo ifup wlan0** works, Hopefully it will stay though. If you added the wep key and it didnt work atfirst it may have not refreshed the changes until you did something else which caused the newtworking to refresh.

Glad you got it going.

---

### Post by DarkDancer on 2005-12-30
I rebooted and it worked well... ;)

Thanks for the help! :smile:

---

