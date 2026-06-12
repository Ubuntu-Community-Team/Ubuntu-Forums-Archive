---
title: "Wireless doesn't work with 11.04"
date: 2011-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jcampbellttu on 2011-05-05
Hello!
 
I have a Dell D630 that I have been using 10.10 on for a while. I love 10.10! Anyway, just upgraded to 11.04 and now my wireless doesn't work. I can't pick up any networks. Any suggestions?
 
Thanks!

---

### Post by brandonmcghee on 2011-05-05
Can't get get a screenshot of the drop down menu when you click on the wireless icon?

---

### Post by jcampbellttu on 2011-05-05
> **brandonmcghee said:**
> Can't get get a screenshot of the drop down menu when you click on the wireless icon?
Yes, at work now, but will do so when I get home. Thanks!

---

### Post by brandonmcghee on 2011-05-05
Honestly it probably just shut off your wireless card, look at the keyboard and there should be a button that turns it on, usually on the F3 or F4, looks like a tower.  That has happened to me in the past.

---

### Post by jcampbellttu on 2011-05-05
> **brandonmcghee said:**
> Honestly it probably just shut off your wireless card, look at the keyboard and there should be a button that turns it on, usually on the F3 or F4, looks like a tower.  That has happened to me in the past.
There is a switch on the side to toggle it on or off. The wireless is on, but yes it's as if it is not. I'll take a look to see if there is a function key for it when I get home. It couldn't be something that simple...

---

### Post by walt.smith1960 on 2011-05-05
> **jcampbellttu said:**
> There is a switch on the side to toggle it on or off. The wireless is on, but yes it's as if it is not. I'll take a look to see if there is a function key for it when I get home. It couldn't be something that simple...

If you haven't done so, also left click the network manager icon and make sure the two checkboxes 1)enable networking and 2) enable wireless are checked.  I've seen them become unchecked for no apparent reason and no network.

---

### Post by netopalis45 on 2011-05-05
I am having the same problem with a Dell Inspiron 1501. The function key to turn on wireless does nothing and when I right click on the networking icon it does the same thing that it does when I left click on it. I have even tried removing and reinstalling the Broadcom driver and that did nothing. When I open the Additional Drivers application it tells me that the driver is activated and currently in use.
The screenshot shows the menu I get when I right click on the networking icon. Wired still works but no wireless

---

### Post by jimmybarcelona on 2011-05-05
> **netopalis45 said:**
> I am having the same problem with a Dell Inspiron 1501. The function key to turn on wireless does nothing and when I right click on the networking icon it does the same thing that it does when I left click on it. I have even tried removing and reinstalling the Broadcom driver and that did nothing. When I open the Additional Drivers application it tells me that the driver is activated and currently in use.
The screenshot shows the menu I get when I right click on the networking icon. Wired still works but no wireless

exact same issue here with dell vostro 1500. broadcom driver is enabled. I switch off the hard switch and back on, nothing. right click on the network icon in the bar and shows nothing. It's like wireless doesn't even exist. I can't check or uncheck it, because it doesn't show up. What's strange about that is before I installed the broadcom driver, it said that firmware was missing for the wireless device. now that I've installed the firmware, no sign of any wireless networks. 

Any luck?

---

### Post by cyclone731 on 2011-05-06
> **jimmybarcelona said:**
> exact same issue here with dell vostro 1500. broadcom driver is enabled. I switch off the hard switch and back on, nothing. right click on the network icon in the bar and shows nothing. It's like wireless doesn't even exist. I can't check or uncheck it, because it doesn't show up. What's strange about that is before I installed the broadcom driver, it said that firmware was missing for the wireless device. now that I've installed the firmware, no sign of any wireless networks. 

Any luck?

It's possible the drivers aren't working well with the 2.6.39 kernel if your loading the default I presume. I found the same problem (I think) with my Intel Integrated graphics on my studio 15 so I booted into 2.6.38 and it works great. You might just try that and get it to work. Just go to 'previous linux version' option at the GRUB screen on bootup and select the '2.6.38-8-generic' kernel. 

If that doesn't work then provide some more info and paste the output of these commands into code tags and well see if we can find an issue there.
```

uname -a
ifconfig
iwconfig
lsmod [SIZE="2"](make sure you put into code tags or these will make the post long)[/SIZE]
lspci

```

---

### Post by jimmybarcelona on 2011-05-06
fixed. YES! found the solution at this post:

[http://ubuntuforums.org/showthread.php?t=1653157&page=2](http://ubuntuforums.org/showthread.php?t=1653157&page=2). The post is halfway down by tacasi.

in a nutshell, uninstall bcmwl-kernel-source, then install "firmware-b43-installer" and "b43-fwcutter" in synaptic. restart, worked great.

Oh, and I'm running 64 bit, kernel 2.6.38-8-generic.

---

### Post by amitubun on 2011-05-12
> **jimmybarcelona said:**
> fixed. YES! found the solution at this post:

[http://ubuntuforums.org/showthread.php?t=1653157](http://ubuntuforums.org/showthread.php?t=1653157).

in a nutshell, uninstall bcmwl-kernel-source, then install "firmware-b43-installer" and "b43-fwcutter" in synaptic. restart, worked great.

Oh, and I'm running 64 bit, kernel 2.6.38-8-generic.

The link does not seems relevant.

**But I followed what you said and it worked like a charm on my DELL Vostro 1500 on Ubuntu 11.04  .**

Here are step for total newbes :

1) Go to 'launcher'  by clicking top left ubuntu icon and type "synaptic".
2) click "Synaptic Package Manager".
3) search for "bcmwl-kernel-source" and if installed, mark it for uninstallation and apply.
4) again search for "firmware-b43-installer" and mark it for installation, it would auto select "b43-fwcutter" , let it do so and apply.
5) After above installation restart, and enjoy wireless.

thanks again @jimmybarcelona

 - amit

---

### Post by jimmybarcelona on 2011-05-12
> **amitubun said:**
> The link does not seems relevant.

**But I followed what you said and it worked like a charm on my DELL Vostro 1500 on Ubuntu 11.04  .**

Here are step for total newbes :

1) Go to 'launcher'  by clicking top left ubuntu icon and type "synaptic".
2) click "Synaptic Package Manager".
3) search for "bcmwl-kernel-source" and if installed, mark it for uninstallation and apply.
4) again search for "firmware-b43-installer" and mark it for installation, it would auto select "b43-fwcutter" , let it do so and apply.
5) After above installation restart, and enjoy wireless.

thanks again @jimmybarcelona

 - amit

You're right, I messed up the link. The link pointed to the right thread, but the wrong page of the thread. I've fixed it. Glad it forked for ya!

---

### Post by irv on 2011-05-12
I don't know if your problem is fixed because this thread is not marked solved. I have a Dell inspiron 1521 and I had problems with my wireless also. I found the solution and here is a link to that thread:
[http://ubuntuforums.org/showthread.php?t=1742147&page=4]("http://ubuntuforums.org/showthread.php?t=1742147&page=4")

---

### Post by jcampbellttu on 2011-05-12
> **jimmybarcelona said:**
> fixed. YES! found the solution at this post:

[http://ubuntuforums.org/showthread.php?t=1653157&page=2](http://ubuntuforums.org/showthread.php?t=1653157&page=2). The post is halfway down by tacasi.

in a nutshell, uninstall bcmwl-kernel-source, then install "firmware-b43-installer" and "b43-fwcutter" in synaptic. restart, worked great.

Oh, and I'm running 64 bit, kernel 2.6.38-8-generic.
This worked perfectly!!!!!

Thanks!!!

---

