---
title: "Clock sync at boot"
date: 2005-05-18
forum: Desktop Environments
---

### Post by apu95 on 2005-05-18
I'm running a laptop which uses the ipw2200 to hook up to the net. I have it configured to go on my home's wlan, so whenever I boot at home it runs fine. The problem is that when I boot somewhere else, it gets stuck for about a minute or two when it tries to sync the time with an ubuntu server (I think its an ubuntu server...if not, its some other server) because it can't find the proper net connection since its not hooked up to my home's wlan. Which file should I edit to disable this syncing of the clock?

Thanks,
Apu

---

### Post by dave9191 on 2005-05-18
[http://www.ubuntulinux.org/wiki/UbuntuBootupHowto/view?searchterm=rc%20update](http://www.ubuntulinux.org/wiki/UbuntuBootupHowto/view?searchterm=rc%20update)

I think that this is the command you want

sudo rm /etc/rcS.d/S51ntpdate

That will stop syncing the clock at boot. You can also manually stop the sync by hitting Ctrl + C during boot. And if you ever want to sync your clock you can always run 

/etc/init.d/ntupdate restart

Dave

---

### Post by nocturn on 2005-05-18
Install rcconf (sudo aptitude install rcconf)
Start rcconf (sudo rcconf)

disable ntpdate

---

