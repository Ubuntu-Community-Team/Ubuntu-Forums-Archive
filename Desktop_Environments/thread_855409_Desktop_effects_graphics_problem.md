---
title: "Desktop effects graphics problem"
date: 2008-07-10
forum: Desktop Environments
---

### Post by mrpjwilson on 2008-07-10
So I was running windows Vista with an ATI Mobility Radeon X1400 graphics card and I installed Wubi on another drive. When I try to turn on the desktop effects it says it cant do it. From what I here this is because of my graphics card. So I was wondering if there is like some patch or something I can install on the ATI site that will let the graphics work in Linux. If this is possible can this be done from my vista, or do I need to be in the linux OS to do it?

thanks
mrpjwilson

---

### Post by helino on 2008-07-11
Have you installed the restricted driver for your graphics card? If you haven't, that's the first thing to do. You can eihter do it by using the "Restricted drivers manager", found in the "System" menu. You can also install them by using Envy. To install Envy, just open the terminal and type:
```
sudo apt-get install envy-gtk
```

You can now install the latest proprietary drivers for your ATI graphics card.

---

### Post by tinny on 2008-07-11
Not sure if its possiable to get your graphics card running under Wubi, but you could show us how it is currently setup by posting the content of your /etc/X11/xorg.conf file. (this will show us what driver your using)

---

