---
title: "enable restricted drivers"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by aldo1234 on 2007-06-12
Hi 

I disabled my nvidia restricted driver, now when i start up ubunut i get a white screen.  I just wanted to know if their is anyway of enabling this driver through the terminal window?

just upgraded to 7.10

Thanks for your help.

---

### Post by LollYouSuckZor on 2007-06-12
```

sudo nvidia-glx-config enable

```

That should do it. :) If not, tell me :D

---

### Post by aldo1234 on 2007-06-12
Hi tested that, says command not found.

Thanks

---

### Post by LollYouSuckZor on 2007-06-12
Command not found eh..

---

### Post by LollYouSuckZor on 2007-06-12
Try this.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nvidia-glx-config enable 


```

Control+Alt+F7

then..  try..

---

### Post by aldo1234 on 2007-06-12
Thanks for your help got it sorted.

The nvidia package must of been removed when i disabled the restricted driver.  Had to install then enable.  

Thanks Again

---

### Post by LollYouSuckZor on 2007-06-12
Sorry I couldn't help. =[

---

