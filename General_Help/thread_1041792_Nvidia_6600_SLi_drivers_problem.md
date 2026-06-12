---
title: "Nvidia 6600 SLi drivers problem"
date: 2009-01-16
forum: General Help
---

### Post by chkh on 2009-01-16
i just installed the ubuntu 8.10 last night on desktop and i'm totally new to linux. the first problem i encounter on my desktop was that ubuntu couldnt automatically find the update for me even after i have activated the version 173.
Going to the desktop effects, i try setting it to normal or extra, ubuntu tells me that i cant have such settings as my graphic card doesnt have the proper drivers to run 3D accelerator on my card.
Then i went and download from nvidia website the linux display driver - IA32. Downloaded, run it, and restarted. Now, i'm stuck in the screen where u press ctrl+alt+f1 to enter(sorry, i really don't know what this screen is called:) i'm really lost when it comes to technological stuff)
Tried following nvidia steps, but nothing is working.

Help Please!!:P

---

### Post by chkh on 2009-01-16
Ohya, forgot to mention that i couldnt boot into my desktop after restarting till now.So i'm stuck now..

---

### Post by MaindotC on 2009-01-16
What is "the version 173"?  When you installed, did you have a wired connection and download all the updates?

---

### Post by chkh on 2009-01-16
The version 173 nvidia driver is suggested by ubuntu when i just installed a fresh copy of the linux. they recomend me to activate this option but still it didnt seem to work.

Yes, my connections were all up and ready to go instantly when i boot into the desktop for the first time. i could surf on mozilla right away :)

---

### Post by MaindotC on 2009-01-16
Did you activate the driver by going to System -> Administration -> Hardware Drivers and select the nVidia driver?

---

### Post by chkh on 2009-01-16
i did not. but how do i get myself back into the desktop from the tty1 screen? :)

---

### Post by MaindotC on 2009-01-16
Hmmm...I'm not sure - I think you can try
```

sudo /etc/init.d/gdm restart

```
If you reboot and the graphics don't work - you should go into something called "Low Graphics Mode".  Press "Continue" and you'll just have a small desktop to work with.  From there you can try different options as well as try installing the nVidia driver.

---

### Post by chkh on 2009-01-16
hmm...the code u gave me isnt effective :) i'm still stuck in the tty1 screen. All the code did was showing two lines of "stopping GNOME display manager" and "starting GNOME display manager" and i'm still stuck here.

My head is spinning from this problem..didnt sleep much. was trying hard to surf for solutions. anyways, thanks for your help strAlan! very much appreciated!

More Help Please!! :)

---

### Post by MaindotC on 2009-01-17
Can you tryl ctrl + alt + f7 to see if GNOME is present?

---

### Post by chkh on 2009-01-17
Nope, nothing is there, just a black screen :)

---

### Post by MaindotC on 2009-01-17
I'm not sure how else to help you as I'm just a novice and I've never had these problems with my ATI card.  You just installed, so I doubt you have any sensitive data on your machine so I'd like to suggest you install 8.04.  In my experience its much more stable.  I'm sorry I can't help you more but I'm not one of those gosu developers that write drivers and can tell you to add or remove lines of code to get it working :(  Try 8.04 - if anything just tthe live cd.

---

