---
title: "classic gnome view even when i login with gnome"
date: 2014-01-11
forum: Desktop Environments
---

### Post by nitin.mahendru88 on 2014-01-11
Hello Everyone,

This is my first post here so if I am doing any mistakes then please pardon me.

I recently bought a new machine the Ideapad y410p and installed 12.04 LTS 64 bit. I have installed gnome on it as I don't like unity. 

The problem is that I still get a classic view of gnome( without the search bar/ application quick view when we drag mouse to top left) even when i select 'gnome' and not 'gnome(Classic)' while logging in. In my earlier machine Acer Aspire 5738, this was not an issue and it gave that easy to use interface in one shot.

Can anybody please help. I am not aware what more information i should share so please hit me and i will share whatever info needed for troubleshooting. 


Thanks

Nitin

---

### Post by deadflowr on 2014-01-12
Do you mean you can't seem to run gnome-shell?
My guess is it's the graphics driver you have which is causing the problem.
Run
```
lspci | grep VGA
```

Gnome-shell is only slightly less of a graphics hog than unity.
So, my bet is it'll run better, if it can, with the closed source drivers.
Post the output of the command above, and we can figure out what to do next.

---

### Post by nitin.mahendru88 on 2014-01-15
/00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev ff)

above is the output of the command lspci | grep VGA. I have tried installing nvidia drivers but sadly they also don't work. I cannot use the optimus feature thus which hurts my battery life too. :/ .

---

### Post by kansasnoob on 2014-01-15
> **nitin.mahendru88 said:**
> /00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev ff)

above is the output of the command lspci | grep VGA. I have tried installing nvidia drivers but sadly they also don't work. I cannot use the optimus feature thus which hurts my battery life too. :/ .

Two graphics chips?

I wondered why this would be useful:

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

I see that's only for 14.04 though which is still in development :(

Should you decide to give 14.04 (Trusty) a try please ask questions here:

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by deadflowr on 2014-01-15
You need to install bumblebee to get the optimus thingy working correctly,
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

as you might read in the link, you'll have to add the ppa for version prior to 13.10.
And as stated by kansasnoob, the development version of Ubuntu, 14.04, will have the prime indicator.

---

### Post by kansasnoob on 2014-01-16
> **deadflowr said:**
> You need to install bumblebee to get the optimus thingy working correctly,
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

as you might read in the link, you'll have to add the ppa for version prior to 13.10.
And as stated by kansasnoob, the development version of Ubuntu, 14.04, will have the prime indicator.

Great info to keep in the old toolbox :^)

---

