---
title: "Compiz in KDE can't login!!!"
date: 2009-02-04
forum: General Help
---

### Post by mpl34 on 2009-02-04
Hey, i just enable compiz instead of kwin then rebooted my machine and now i can no longer log on. After choosing which OS to boot into after grub it loads the required drivers etc. but after this the screen goes black with a few weird lines of colours the backlight then flashes on and off and goes to a screen with a flashing line at the top for writing the process then repeats with the weird lines and backlight. 

So basically i want to know if i can change from booting with compiz to Kwin. I have tried the command > kwin --replace through recovery mode but no luck.

---

### Post by mpl34 on 2009-02-04
Hey i am really getting furstrated with this i'm desperate for help. is there any way to stop compriz from booting to Kwin in the recovery mode screen, i see this as the only solution however i'm new and open for any suggestions

---

### Post by abn91c on 2009-02-04
> **mpl34 said:**
> Hey i am really getting furstrated with this i'm desperate for help. is there any way to stop compriz from booting to Kwin in the recovery mode screen, i see this as the only solution however i'm new and open for any suggestions
removing compiz may be your only option
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```then you can try kwin --replace again or just reboot

---

### Post by mpl34 on 2009-02-04
Hey thanks for the reply unfortunately i never solved the problem at least i don't think i did, however i booted my pc in recovery mode used the root terminal to start kdm which took me to my login screen, however the keyboard and mouse didn't respond then restart the pc and my login screen showed up as usual.

I did run the commands u gave me above but got an error message telling me that they were not installed even tho i thought they came pre-installed with kubuntu

thanks,

---

