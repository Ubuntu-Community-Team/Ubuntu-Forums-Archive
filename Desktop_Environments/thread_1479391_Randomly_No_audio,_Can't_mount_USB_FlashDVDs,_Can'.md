---
title: "Randomly: No audio, Can't mount USB Flash/DVDs, Can't shutdown"
date: 2010-05-10
forum: Desktop Environments
---

### Post by phartiphukborlz on 2010-05-10
I have just installed Lucid i386 on an intel Core2Duo. Everything seems to be OK but about a third of the times I boot the system the following happen:

1) aplay -l reports no soundcards found and therefore I have no sound whatsoever
2) I cannot mount any USB Flash drives or DVD discs and I keep getting "Not authorized" error messages plugging them in.
3) The system won't reboot/shutdown by the gnome applet. Instead, it will drop back to the login screen asking my login. Furthermore, it won't even shutdown from there! Only a poweroff or reboot from command line can work.
4) The gnome applet "Indicator applet session" only shows "Log out, Restart, Shutdown". Suspend and Hibernate options are missing.

Furthermore, it seems that I am the only one who has these issues. My sound card is an onboard HDA Intel although this seems to be that something else dies taking some major subsystems down with it. Any ideas? 

/proc/asound/cards shows:
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe028000 irq 23

but: aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by phartiphukborlz on 2010-05-10
by the way, this is my lshw

---

### Post by Fisaulerod on 2010-05-18
Same problem.

---

### Post by yourself on 2010-05-19
I think I have managed to circumvent it (which means that in the last 10 reboots this behavior was not encountered) by:

-> Upgrading the BIOS of my nforce2 motherboard
-> Disabling the onboard LAN controller (I use atheros wireless, so I don't need it)
-> Blacklisting nforce_i2c module
-> Disabling C1E and intel Speedstep from my motherboard

I really don't know what or if had any effect.... Hope it helps you

---

### Post by Fisaulerod on 2010-05-22
> **yourself said:**
> I think I have managed to circumvent it (which means that in the last 10 reboots this behavior was not encountered) by:

-> Upgrading the BIOS of my nforce2 motherboard
-> Disabling the onboard LAN controller (I use atheros wireless, so I don't need it)
-> Blacklisting nforce_i2c module
-> Disabling C1E and intel Speedstep from my motherboard

I really don't know what or if had any effect.... Hope it helps you

I don't how to do that :/.

---

### Post by jejemon on 2010-05-23
I have this ongoing problem since I installed Ubuntu 8.10 where in I can no longer use my flash drive or 
any other USB media devices. I thought it will be resolved once the new version of OS is released but I
already installed 10.1 and still the same issue is happening.

[sliding shelves Denver](http://www.shelfgenie.com/blog/sliding-shelves-denver)
[Conference Tables](http://www.eqaofficefurniture.com/conference-tables-cat-300.html)

---

### Post by saias on 2010-05-23
just got the exact same problem out of nowhere... plus my video-card drivers are not working and there are no proprietary drivers on the hardware drivers section. I think its the last upgrade i did this morning. 

any ideas???

its amazing how bad is the 10th version..

---

### Post by saias on 2010-05-23
one of the above solutions worked for me.

You have to blacklist nforce by adding on the end of the blacklist configuration file the line below:

blacklist nforce_i2c

open the file by running

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

on the terminal and then save it. 

```
sudo reboot
```

and everything should be fine. The graphic drivers need to be reinstalled if you have graphic problems as i did otherwise with the above everything should be fine.

---

### Post by ogduartev on 2010-05-26
After last upgrade I got the same problem here, but I have found an uggly solution:

- Open konqueror and explore the usb flash (konqueror will mount it!!!)

---

### Post by Fisaulerod on 2010-06-16
> **saias said:**
> one of the above solutions worked for me.

You have to blacklist nforce by adding on the end of the blacklist configuration file the line below:

blacklist nforce_i2c

open the file by running

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

on the terminal and then save it. 

```
sudo reboot
```

and everything should be fine. The graphic drivers need to be reinstalled if you have graphic problems as i did otherwise with the above everything should be fine.

I did that but the problem remains :/.

---

### Post by BiGViC340 on 2010-06-22
I have the same problem and have a ATI Radeon 9800 Pro so is not an Nvidia issue

---

