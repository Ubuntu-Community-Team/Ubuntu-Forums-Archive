---
title: "Transparent Terminal"
date: 2011-05-26
forum: Desktop Environments
---

### Post by pcarlos853 on 2011-05-26
Hi All!,

I have been running Ubuntu 10.10 for quite some time now, however I remember in older versions of Ubuntu Desktop the terminal could be made transparent so you could see what was behind it. But for some reason on Ubuntu 10.10 I can make the terminal transparent, however I cant see the windows behind it all I see is the background. Anyone know how to fix this?

Thanks
Carlos

---

### Post by sanguinoso on 2011-05-26
Go to (In a terminal) Edit -> Profile Preferences -> Background and then select transparent background.

---

### Post by pcarlos853 on 2011-05-26
Hi Sanguinoso,

I have done that, however my goal is to see what ever is open behind the terminal not my desktop wallpaper.

P.S. I know that there was a way to do this in older versions of Ubuntu

Thanks
Carlos

---

### Post by sanguinoso on 2011-05-26
Ah, I didn't grasp that from your first post. The background looked black so I thought transparency was unset. My system behaves as you want it to by default. Have you installed any different window managers or decorators?

---

### Post by teachop on 2011-05-26
Do you have desktop effects enabled?

---

### Post by Maheriano on 2011-05-26
You need to enable Compiz I think, and maximize your graphic display setting thing.

---

### Post by pcarlos853 on 2011-05-26
Changing my Desktop visual effects to normal made it work.

Thanks!
Carlos

---

### Post by Krytarik on 2011-05-26
To achieve the same just with Metacity, enable its compositing option:
```
gconftool-2 /apps/metacity/general/compositing_manager --type bool --set true
```
Greetings.

---

