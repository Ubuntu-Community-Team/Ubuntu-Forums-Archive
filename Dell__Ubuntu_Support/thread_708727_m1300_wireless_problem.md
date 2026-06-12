---
title: "m1300 wireless problem"
date: 2008-02-26
forum: Dell  Ubuntu Support
---

### Post by tdansel88 on 2008-02-26
I'm very new to linux and I'm having some wireless issues. I have intel 3945 wireless card and my driver was preinstalled on ubuntu. Right now when I got to network connections I can alter my wireless properties and even see available networks. When I try to connect to a network I should have access to, no connection gets established and no errors display.  Also, my xps 1330 has a led light that tells you when the wireless is on or off, instead of being lit or not lit, mine is flickering. any help would be appreciated, keeping in mind i'm new to linux

---

### Post by notwen on 2008-02-27
The module loaded into Gutsy does not work all that well and is very unstable.  Dell has made a workaround found [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues").  Post back if you have trouble understanding these instructions.  Also after making the changes, you may notice that your LED light for your wifi will no longer light up, that's normal.  Your wifi will still work just fine.

---

### Post by tdansel88 on 2008-02-27
i got most of it, i don't know where to run the command $ lsmod | egrep 'Module|iwl|ipw' . i put it through the terminal and it said file not found.

---

### Post by tdansel88 on 2008-02-27
sorry, the terminal said command not found

---

### Post by notwen on 2008-02-27
> **tdansel88 said:**
> sorry, the terminal said command not found

You may have included the $, try the following in terminal:

```
$ lsmod | egrep 'Module|iwl|ipw'
```

---

### Post by pormogo on 2008-02-28
I've tried using dells fix to try and fix the issues my m1330n is having when resuming from suspend or hibernate. As I have seen in a few threads people are saying that the ipw3945 modules is spotty in general. However after correctly loading the iwl3945 module my computer completely stops seeing wireless access points when coming back from a suspend or a hibernate, essentially meaning with the iwl module putting my computer into my backpack means when I boot back up I am going to have to reload whatever wireless driver I am using just to get my connection working (and sometimes network monitor doesn't ever seem to want to come back and I am stuck using iwconfig to connect to stuff). I've seen a few posts on this so far but still no fix :( This is all kinds of annoying having to micromanage the drivers for my wireless card every time I want to use my laptop.

---

### Post by pormogo on 2008-03-05
This is REALLY starting to annoy me. Netowrk manager does not seem to want to play nicely with the iwl3945 module. The ipw3945 module seems to be pretty broken. It intermittently drops my signal strength to 0 and then cannot join any wireless networks. Resatrting Network manager doesn't do anything, and *modprobe -r ipw3945* just causes the terminal to hang and hang. I am basically stuck rebooting. The iwl3945 modules seems to work much better and doesn't intermittently drop the same way. However it also doesn't detect any network after coming back from a suspend or hibernate. Reloading the iwl module does not fix that issue either. How can I get functional wireless on my m1330n?

---

