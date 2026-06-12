---
title: "Vodafone Connect"
date: 2009-04-15
forum: General Help
---

### Post by Gabt on 2009-04-15
Cant seem to get Vodafone Connect to install on ubuntu HH (8.04)

vodafone-mobile-connect:
 Depends: usb-modeswitch  but it is not installable

I have found a usb-modeswitch.deb on the net, infact 2 versions, and installed them both, but it still returns that error message. Everything else on the laptop is working flawlessly, would be nice to use my mobile broadband when im out n about tho.


The braodband isnt even a USB device, its just a sim card in the back on the laptop behind the battery (Maybe its connect by USB internally, i dunno)

Anyone know how to fix this?

```
kev@ubuntu:~$ sudo apt-get install vodafone-mobile-connect
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  vodafone-mobile-connect: Depends: usb-modeswitch but it is not installable
E: Broken packages

```

Any help appreciated.

---

### Post by Gabt on 2009-04-15
bump bump

---

### Post by Gabt on 2009-04-15
Seriously, no one knows?

---

### Post by cviorel on 2009-04-15
My guess is that the package is corrupted in some way.
You should try another package. You may want to take a look here:
```
https://forge.betavine.net/frs/?group_id=12&release_id=19
```

---

### Post by marks_linux on 2009-04-15
not sure how much this helps, but Vodafone (VMC) card wouldn't work without lots of effort in 8.04. But worked out of the box so to speak in 8.10

---

### Post by Gabt on 2009-04-15
I tried II initialy, but it took absolutley ages to install, then it had no packages! i mustve screwed it somehow, anyway, ive managed to get VMC installed now, however.
```
kev@ubuntu:~$ vodafone-mobile-connect-card-driver-for-linux 

Failed to load application: [Errno 2] No such file or directory: '/home/kev/.vmc2/vmc.cfg'
kev@ubuntu:~$ 
```

Thanks to the guy who pointed me toward the usb-modeswitch package btw, thnx.

Anyone know how to cure this error now?

---

### Post by Gabt on 2009-04-15
Bump again, 
sorry for being impatient been at this fior ages though

---

### Post by Sealbhach on 2009-04-15
What kind of modem have you got? You probably don't need this since Ubuntu 8.10 supports most 3G usb modems like the Huawei E220 etc.
 
 
.

---

### Post by Plumtreed on 2009-04-15
You will find that it works with version 8.10 without any hassle. You could stay with 8.04 and upgrade NetworkManager.

The following will show you how to upgrade. 

[http://ubuntuforums.org/showthread.php?t=797059&highlight=howto+network+manager+hardy](http://ubuntuforums.org/showthread.php?t=797059&highlight=howto+network+manager+hardy)

---

### Post by Gabt on 2009-04-15
There is no USB modem, its just a sim card inside the laptop.

Did the network manager update and still cant connect, i love ubuntu, but im gonna HAVE to go back to windows (sigh).
Been at this for absolutley ages, its beginning to ruin my faith in ubuntu, and we cant have that now!

---

