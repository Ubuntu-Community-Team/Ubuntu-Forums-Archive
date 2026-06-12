---
title: "Changing graphics card question"
date: 2009-06-03
forum: General Help
---

### Post by badgaz1 on 2009-06-03
I have an ATI graphics card in my parents computer and I put Ubuntu on it yesterday and it was the first time I had the pleasure to experience the truly awful performance of ATIs Linux drivers so I'm going to be putting a Nvidia graphics card in it.

Are there any precautions I should take to avoid messing up my Ubuntu installation (Jaunty) or can I just uninstall the ATI driver, turn off the computer, switch graphics cards and all should be well?

---

### Post by doas777 on 2009-06-03
> **badgaz1 said:**
> I have an ATI graphics card in my parents computer and I put Ubuntu on it yesterday and it was the first time I had the pleasure to experience the truly awful performance of ATIs Linux drivers so I'm going to be putting a Nvidia graphics card in it.

Are there any precautions I should take to avoid messing up my Ubuntu installation (Jaunty) or can I just uninstall the ATI driver, turn off the computer, switch graphics cards and all should be well?

well one thing that may make your transition smoother, is to disable any ati drivers before you take the card out. easiest was is to run 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bu.ati
sudo dpkg-reconfigure -phigh xserver-xorg

```to backup your existing xorg, and then reset it to default. reboot once, and then shutdown to replace your card.

good luck

---

### Post by badgaz1 on 2009-06-03
Thank you for that.

---

### Post by VastOne on 2009-06-03
> **badgaz1 said:**
> Thank you for that.

I would also make sure to have the latest nVidia drivers in case you run into any issues and need to install them from a pre boot situation.

---

