---
title: "Compiz Fusion installation / video card"
date: 2008-03-05
forum: Desktop Effects &amp; Customization
---

### Post by terrorsathan on 2008-03-05
Hi,

I'd like to know if Compiz Fusion would work with the video card I have (see signature).
I hope for an answer.

Thanks

---

### Post by blazercist on 2008-03-05
yes

---

### Post by terrorsathan on 2008-03-05
Ok, thanks for your answer.
I'll try to install it now and come back if I'm having problems.

---

### Post by terrorsathan on 2008-03-05
I just removed ubuntu from my 20 GiB partition to reinstall it correctly (I've changed a lot in the system settings, so I wasn't sure if compiz fusion would work with this settings - to be sure I'm re-installing ubuntu now).

When I get to the "Prepare partitions" step in the ubuntu installation wizard, I get the following warning message:
```
File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 32043 (63962 expected); size of FATs is 126 sectors (250 expected).
```
What does that exactly mean?

Anyway, when I click on 'ignore' the following warning message appears:
```
You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory.

If you do not go back to the partitioning menu and assign a swap partition, the installation will continue without swap space.
```
Now I'm kinda confused ... do I really need a swap partition with the 3GiB RAM I have?

Actually I can continue the installation, but I'd like to do everything correctly, so I'm going to wait for an answer now.
Thank you.

---

### Post by terrorsathan on 2008-03-05
Looks like I've solved this problem now. Anyway, I posted it in the wrong forum ;).

Now I have a new question:
When I'm trying to activate the *Extra* effects in the 'Visual Effects' tab of the 'Appearance Preferences', the following error message is returned:
```
Desktop effects could not be enabled
```

Why can't I enable those extra effects? Is it because of my video card?

Command compiz in the terminal returns:
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

I hope for an answer, thanks,

---

### Post by blazercist on 2008-03-06
you need to install the restricted drivers for your video card

system>administration>restricted drivers manager 

check the box next to your video card, it will either prompt you to restart your x server or it will do it automatically, in any case you need to restart your X server, if you dont know how to do that then i just recommend restarting once you've enabled the driver

---

