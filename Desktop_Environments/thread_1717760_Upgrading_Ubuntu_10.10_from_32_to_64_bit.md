---
title: "Upgrading Ubuntu 10.10 from 32 to 64 bit?"
date: 2011-03-30
forum: Desktop Environments
---

### Post by Mrich1976 on 2011-03-30
Is there a way to upgrade from Ubuntu 10.10 32 bit to Ubuntu 10.10 64 bit, without doing a complete reinstall?

I've got several apps on my machine that I don't want to have to re-download, and some things set up a certain way that I don't really want to have to re-configure.

So, can I upgrade to 64 bit without losing my apps or settings?

---

### Post by Kirboosy on 2011-03-30
It is possible but honestly its easier to do a fresh install. 

Take a look [here]("http://ubuntuforums.org/showthread.php?t=765428")


You also might want to look at [PAE]("https://help.ubuntu.com/community/EnablingPAE")

That's the closest thing you will get to 64 bit without reinstalling.

~Caboose

---

### Post by 3Miro on 2011-03-30
Make a reinstall, to get full advantage of 64-bit you will have to redownload the 64-bit versions of all your programs anyway (otherwise it makes no sense to use 64-bit kernel and run 32-bit apps on it).

PAE is 32-bit, but it allows you to use 4GB of RAM. If this doesn't work for you, do a reinstall.

---

### Post by meandtheboys55 on 2011-03-30
:) I did a fresh install as I could not find a easy way to do it...

---

### Post by Mrich1976 on 2011-03-30
Ok. Thanks everyone. Looks like a re-install might be the way to go...Ugh...

---

### Post by geiroffenberg on 2011-04-08
Hi guys, i just want to say i just did a upgrade from 32 to 64 to match my 64 amd chips, but i did the innstall using a usb stick and chose the partition manually, chose ext4, mountpoint / and did not format it. That way i kept the home. It worked great.
I had to reboot twice before the internet modem worked for some reason, but everything works now, and the performance is noticable increased. everythings seems faster and snappier.
I noticed it DOES use quite a lot more ram now. It first tried to run it with  500meg ram and it uses swap more or less all the time. Somemusic apps did not work or was way to slow becuase of lack of ram. You need at least a gig. But it costs like 20 bucks or so so it shouldnt be a problem for most ppl.

---

### Post by 3Miro on 2011-04-08
> **geiroffenberg said:**
> Hi guys, i just want to say i just did a upgrade from 32 to 64 to match my 64 amd chips, but i did the innstall using a usb stick and chose the partition manually, chose ext4, mountpoint / and did not format it. That way i kept the home. It worked great.
I had to reboot twice before the internet modem worked for some reason, but everything works now, and the performance is noticable increased. everythings seems faster and snappier.
I noticed it DOES use quite a lot more ram now. It first tried to run it with  500meg ram and it uses swap more or less all the time. Somemusic apps did not work or was way to slow becuase of lack of ram. You need at least a gig. But it costs like 20 bucks or so so it shouldnt be a problem for most ppl.

I wouldn't use 64-bit on anything with less than 2GB of RAM. Any speed advantage that you can get from 64-bit is negated from the higher memory usage and the use of Swap.

---

