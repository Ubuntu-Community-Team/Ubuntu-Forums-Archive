---
title: "nVidia driver is driving me crazy"
date: 2009-06-16
forum: General Help
---

### Post by papajonesy on 2009-06-16
Hello. I installed the nvidia driver for my 9800GTX+ through the drivers utility in ubuntu and now whenever i try to boot into ubuntu it doesn't give me a desktop. its just kind of like a terminal. it asks me for my username and password but i don't get an actual GUI. Please help, it would be much appreciated.

---

### Post by madnessjack on 2009-06-16
Hi,

In the terminal, log in, and type
```
sudo dpkg-reconfigure xorg-xserver
```
And that will reset the driver back to what it was. Then you need to figure out what went wrong.
I recommend taking a look at this link
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

It looks rather promising

Hope this helps

---

### Post by papajonesy on 2009-06-16
thanks for the quick response. it said the package wasn't installed when i input the command. i have used evnyNG before but with the same result. i just reinstalled ubuntu because i have been having this problem nonstop in kubuntu and ubuntu and i give up. forget nvidia drivers, although it would be nice it is not worth the sacrifice for me.

---

### Post by madnessjack on 2009-06-16
```
sudo dpkg-reconfigure xserver-xorg
```

Sorry, I got it wrong, that's the correct command - I'm new here too ;)

That resets your drivers back to the original. I'm having the same problem, I cant get nvidia drivers to work. If I figure out how to fix it, I'll let you know!

---

### Post by papajonesy on 2009-06-17
alright thanks man. i am guessing for me it may be a problem with me have 2 9800GTX+ in SLI so i think it is causing some issues in linux but i'm not certain.

---

### Post by papajonesy on 2009-06-17
i tried installing it again but this time i'm stuck at a screen that isn't a terminal it says this

*Starting Avahi mDNS/DNS-SD Daemon avahi-daemon               [OK]
*Starting Common Unix Printing System: cupsd                          [OK]
*PluseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
*Starting System Tools Backends system-tools-backends            [OK]
*Starting anac(h)ronistic cron anacron                                       [OK]
*Starting deferred execution scheduler atd                                 [OK]
*Starting periodic command scheduler crond                              [OK]
*Enabling additional executable binary formats binfmt-support
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
                                                                                              [OK]
*Checking battery state...                                                         [OK]



The asterisk on the pulseaudio line is orange but the rest are white. This is what I have been getting everytime i try to install nVidia drivers on ubuntu and kubuntu. If anyone can help me I would be the most greatful man on the planet. Thank you.

---

### Post by martin_legion on 2009-06-17
YOU ARE NOT ALONE.
Sorry no help about this.

---

### Post by papajonesy on 2009-06-17
alright. so basically, i have to reinstall? awesome. 5th reinstallation this week. oh well, i hope there will be a working driver soon. i want my visual effects back like i did back in feisty fawn.

---

