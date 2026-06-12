---
title: "ubuntu with kubuntu-desktop running beryl"
date: 2006-11-03
forum: Desktop Environments
---

### Post by BKK on 2006-11-03
I hope this is the right place... 

I did a fresh install of Edgy, then I installed beryl and kubuntu-desktop with not real problems. ( I like to use some kubuntu programs too) The thing is now when I reboot I see the kubuntu loading screen then the ubuntu splash login screen. I am not sure where to change so I can put the Ubuntu one back.

---

### Post by d3v1ant_0n3 on 2006-11-03
So If I'm right, you're seeing the Kubuntu usplash (loading progress) instead of Ubuntu's?

I installed kubuntu-desktop package the other day, then removed it (decided to try Gnome for a while), and discovered that I was stuck with Kubuntu's usplash.

I search in synaptic for 'usplash', ensured I had removed Kubuntu's usplash, and reinstalled the ubuntu one.

The packages are 'kubuntu-artwork-usplash' and 'usplash-theme-ubuntu'

You might just be able to fix this with 'sudo dpkg-reconfigure gdm', which will bring up a dialog to allow you to select which DM to use-Kubuntu's or Ubuntu's.


Hope one of these suggestions worked.

---

### Post by BKK on 2006-11-03
In synaptic when I go to remove the kubuntu-usplash thing it say that I must uninstall the kubuntu-desktop as well. I want to keep it. I like using some of the programs that come with it. I can use them when I use the GDM but i think they will disappear when I uninstall the kubuntu-desktop. Anyways its not a big deal beryl is great! Thanks

---

### Post by drr422 on 2006-11-03
You can remove the kubuntu-usplash thing and kubuntu-desktop.  Kubuntu-desktop is just the name of the package that binds all of the kubuntu programs together, basically it serves no purpose after you have installed it.  What you need to worry about is if it trys to uninstall all of the programs that come with kubuntu-desktop.  If it tries to do that, then stop.  But you will be safe to remove the kubuntu-desktop.  As soon as you try to remove anything that came with kubuntu, then it would also show you needing to remove kubuntu-desktop.  For instance, if you didn't like kmix, and you wanted to remove it, it would remove kubuntu-desktop as well.  I hope this helps.

---

### Post by BKK on 2006-11-03
Excellent help! Thanks you all! I uninstalled the kubuntu usplash and reinstalled the ubuntu one. That did the trick!

---

