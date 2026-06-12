---
title: "Completely removing KDE &amp; Xfce"
date: 2009-06-26
forum: Desktop Environments
---

### Post by pizza-is-good on 2009-06-26
Hello everyone

I am somewhat new to Ubuntu, only have about 6 months of experience with it. After a while of having it I decided to try out KDE and Xfce. At the time I was using 8.10.

I have now updated to 9.04, and decided to stay with GNOME, and I am trying to un-install both KDE and Xfce. I went through Synaptic, and completely removed the same packages that I used to originally get both desktops. It somewhat worked, but I still got things from both desktops randomly, mainly the ubuntu loading bar at startup and shut down, which is kubuntu's. :confused:

Then I went through Synaptic and completely removed everything that was KDE related. After that, the shut down loading bar is back to normal, but not the start up one.
I am cluless on what to try next, so any advise on how to completely get rid of all the KDE and Xfce everythings will be appreciated.

Thanks.

---

### Post by merlinus on 2009-06-26
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by pizza-is-good on 2009-06-26
I executed both commands, and they took care of everything.... except for that very annoying Kubuntu load bar at start-up.

One the bright side, it seems to be running faster now:D

Anyone else have any other ideas?

Thanks

---

### Post by pizza-is-good on 2009-06-26
OK, I solved it!
I did need to 'restore' GNOME, but since that didn't do it, I kept looking.
I had installed the Start-Up manager, to take care of my Grub, since I didn't want to be using KGRUB Editor. (I had no idea that this would help me solve it)
Anyway, after I 'destroyed' KDE & Xfce with the commands that merlinus gave me, the Usplash (I didn't know that the loading bar was called that, or else, a quick google search would have done the job) for Kubuntu was still the one showing.
So after searching around for a while, I found out that the loading bar was reffered to as the Usplash, and then I was able to look for it in Synaptic.
The next problem that I found was that the onlu Usplash that I had installed was the regular Ubuntu one, and the Kubuntu one wasn't :confused:. So I completely removed the Ubuntu one, rebooted (maybe I didn't have to reboot, but being used to Windows....), then downloaded the ubuntu Usplash and went to the Start-Up Manager to select it. (I had by then already found the Usplash option in the Manager). I then rebooted (This time just to see if it had worked), and it did.

Problem solved! I hope that this information is valuable to some newie like me in the future....

---

