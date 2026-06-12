---
title: "Change Ipod Mount Point"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Pooch on 2006-08-30
I have Amarok installed, and an Ipod mounted at /media/ipod. For Amarok to detect an Ipod it needs to be mounted at /mnt/ipod. Is there a way I could get my Ipod to be mounted at /mnt/ipod by default? Or should I change the mount command in Amarok?

---

### Post by lnxpwr on 2006-08-30
changing the mount command in amarok would be the best way i guess. but you can also try to make a softlink:
```

sudo ln -s /media/ipod /mnt/ipod

```

---

### Post by Pooch on 2006-08-30
What should I change the mount command to in Amarok? I'll try the softlink now.

Edit: Softlink didn't work. I get the same error "Could not find device, please mount it and try again" My ipod is mounted to /media/ipod.

---

### Post by lnxpwr on 2006-08-30
sorry, thought a softlink would help ;-( ...
under amarok-settings-configure amarok-collection you can choose your directory...

---

### Post by Pooch on 2006-08-30
When I try to transfer songs onto my Ipod Amarok says that it's not mounted. That's because Amarok's looking for my iPod in the /mnt/ipod folder. By default, iPod's get mounted to /media/ipod. Is there a way I could change where the iPod get's mounted by defaut?

---

