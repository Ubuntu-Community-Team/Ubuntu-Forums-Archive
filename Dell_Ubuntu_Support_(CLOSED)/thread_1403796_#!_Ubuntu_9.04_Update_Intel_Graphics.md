---
title: "#! Ubuntu 9.04 Update Intel Graphics?"
date: 2010-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamitsukai on 2010-02-10
I'm currently running Crunchbang Linux (based on Ubuntu 9.04 'Jaunty' but with openbox) on a Dell Inspiron 1525 however the intel graphics are a let down to say the least... choppy videos and unplayable full screen flash

so I was wondering if it was possible to install newer drivers...?

Thanks in advance =]

output from 'lspci' tells me I have the following on-board graphics:

```
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev  0c)
```

---

### Post by coffeeaddict22 on 2010-02-10
Hi,
Intel drivers were in a state of major rewrite(read "disrepair") for much of last year.  If you google around you'll see it.  Your best bet by far is to upgrade to a 9.10 derivative.

---

### Post by ownasaur on 2010-02-11
I have an Inspiron 2200 and had similar issues about the video drivers not working (intel) in earlier ubuntu releases... I tried 9.10, ran the updates and everything worked fine. :D

---

### Post by kamitsukai on 2010-02-11
Yes unfortunately Crunchbang skipped the 9.10 release in preference to going all out on the LTS however there has been good feedback from using the Crunchbang install script on a 9.10 base install...hmmm

maybe this would be a good time to get to know Debian (^_^)

---

### Post by coffeeaddict22 on 2010-02-11
I just did a dual boot with debian on my laptop.  It's nice.  

USB key install works fine, although I'd advise using the CD download and not the network one; with the network download, my network card wasn't recognised so I had to go back and get the bigger file anyway.
 
Biggest issue was with wifi.  There's a network setup interface in the Admin menu, but it adds the info to /etc/network/interfaces, which is a good way of making sure NetworkManager can't see the interface.  If there's anything other than the two lines regarding lo in there, NetworkManager won't autoconfigure your network; the trick was to delete the unwanted lines in the e/n/i file, and then configure through the taskbar icon, which accesses NetworkManager directly.

---

### Post by kamitsukai on 2010-02-12
> **coffeeaddict22 said:**
> I just did a dual boot with debian on my laptop.  It's nice.  

USB key install works fine, although I'd advise using the CD download and not the network one; with the network download, my network card wasn't recognised so I had to go back and get the bigger file anyway.
 
Biggest issue was with wifi.  There's a network setup interface in the Admin menu, but it adds the info to /etc/network/interfaces, which is a good way of making sure NetworkManager can't see the interface.  If there's anything other than the two lines regarding lo in there, NetworkManager won't autoconfigure your network; the trick was to delete the unwanted lines in the e/n/i file, and then configure through the taskbar icon, which accesses NetworkManager directly.

Thanks, I had a feeling that wifi would be the 'major' hurdle as even in Ubuntu I have to use the Broadcom STA Driver

in fact on many occasion I've thought of ripping out the broadcom wifi and replacing it with a nicer supported card not really gonna  cost any more then say £20-30, still might be fun fiddling with Debian :D

---

### Post by Greyed on 2010-02-13
> **coffeeaddict22 said:**
> Intel drivers were in a state of major rewrite(read "disrepair") for much of last year.  If you google around you'll see it.  Your best bet by far is to upgrade to a 9.10 derivative.

In my experience (10v, 945GME) those drivers are still in a major state of disrepair.  I wish we could get the 8.04 drivers in 9.10 just to see if it is an Intel driver regression or a kernel regression that has my video performance in the crapper.

---

### Post by bobcollard on 2010-02-16
You might give another Ubuntu offshoot a try.  Linux Mint puts out a version 8 called Fluxbox that is similar to open box.  It is in tune with Ubuntu 9.10.   I think it has better graphics.  Download and burn the Live CD and try it.  Here's their main link:
[http://www.linuxmint.com/index.php](http://www.linuxmint.com/index.php)

---

