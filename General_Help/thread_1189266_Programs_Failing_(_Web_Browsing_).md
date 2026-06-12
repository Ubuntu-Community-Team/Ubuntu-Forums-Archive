---
title: "Programs Failing ( Web Browsing )"
date: 2009-06-16
forum: General Help
---

### Post by nexoncore on 2009-06-16
I recently updated my copy of ubuntu 9.04, the update involved a firefox update. Everything went fine duing installation, but when I came to open firefox, I got a lot of errors.

Thinking it may just be an ubuntu error, I rebooted my computer. Now every time I click Firefox, It brings up a bar at the bottom stating "Starting Firefox we....". But when that disapeer's, firefox is not loaded. I tried uninstalling, reinstalling and even complete removal and install fresh, but none of this worked.

Ontop of that, I downloaded several other Web Browsing applications but none of them would load.

Is there any fix for this, preferably I dont want to reinstall ubuntu as I have a 10gig torrent I am 70% through downloading and dont want to go from start again.

FYI, the transmission ( Torrent ) program, can access the internet and still download the torrent.

---

### Post by TrakerJon on 2009-06-16
In a terminal window **sudo apt-get --purge remove firefox**

Delete the .mozilla folder in your home directory then reinstall firefox.

In a terminal window **sudo apt-get install firefox**

It's possible you may have gotten a kernel update that didn't go as expected.

---

### Post by nexoncore on 2009-06-16
It has not worked, I am scared to think it may be a virus of some sort, but I dont even know if there are ubuntu viruses or even antivirus software.

---

### Post by Celauran on 2009-06-16
It's not a virus.

---

### Post by nexoncore on 2009-06-16
Well, the method above did not work. I used the tools on boot to try and sort it, to no avail.

---

### Post by hyperdude111 on 2009-06-16
I have posted this on a few firefox threads and it has worked so i'll try again here.
> 
Go to Home the press "ctrl-H" go into the .mozilla folder.

rename the firefox folder to firefox.bak and it should work.


This is NOT a virus, there are no Linux viruses that you are likeley to EVER come across. [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses) This is a firefox related issue. Just for future reference, if you have a problem with linux/ubuntu it is NOT a virus, or any other type of malware.

---

### Post by Celauran on 2009-06-16
```
cd
rm -rf .mozilla
firefox
```

If it spits out errors, please copy them here.

---

### Post by nexoncore on 2009-06-16
Why am I getting errors with several browser then if its a firefox issue. 

Im logging off for the night, I will let you know how things pan out in the morning.

Thank's for everyones support thus far

---

### Post by nexoncore on 2009-06-16
Terminal Froze, tried again and it did not list errors but problem persists. 

If I reinstall ubuntu, will it transfer my saved data over and program preferences. Im going to leave the torrent I mentioned to download over night and hope its done in the morning.

---

### Post by jsanbor1 on 2009-06-16
Thanks Celauran  - my Firefox was crashing like crazy after I installed the Nvidia driver.  Now it seems to be working fine.

what does this do?

```
cd
rm -rf .mozilla
firefox
```

it seems like that fixed it?  

(I just installed Ubuntu for the first time for my HTPC.)

---

### Post by nexoncore on 2009-06-17
I restarted the computer this morning, and now I am getting an error on load stating it must load in low graphic. Just whacked in the Live CD which is working perfectly, so I will just have to reinstall.

Thanks for everyones advice.

---

