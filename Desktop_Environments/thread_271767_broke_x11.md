---
title: "broke x11"
date: 2006-10-05
forum: Desktop Environments
---

### Post by werty on 2006-10-05
Hi

I messed up with my x11 setting and i dont have a backup of the conf file. I cannot goto the graphical logon, everything is text based.
What should i do?

Thanks in Advance

---

### Post by Kateikyoushi on 2006-10-05
login and try this

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bigken on 2006-10-05
> **Kateikyoushi said:**
> login and try this

```
dpkg-reconfigure xserver-xorg
```

its sudo dpkg-reconfigure xserver-xorg ;)

---

### Post by werty on 2006-10-05
Hi

error:
package 'xserver-org' is not installed and no info is available

Any other way?

Thanks in Advance

---

### Post by bigken on 2006-10-05
> **werty said:**
> Hi

error:
package 'xserver-org' is not installed and no info is available

Any other way?

Thanks in Advance

its sudo dpkg-reconfigure xserver-xorg not **org**

---

### Post by werty on 2006-10-05
hi
My bad. I ll try it..

Thanks

---

### Post by Kateikyoushi on 2006-10-05
> **bigken said:**
> its sudo dpkg-reconfigure xserver-xorg ;)

Ah yes, I need to get used to it.
Thanks.

---

### Post by werty on 2006-10-05
Hi
The reconfigure was complete but x11 did not work.
error:
couldnt open RGB_DB '/usr/share/X11/rgb'

ubuntu books graphically but then this error turns up
with a blue screened err msg.

edit: I messed up with x11 conf files when trying to install XGL

Thanks in Advance

---

### Post by werty on 2006-10-05
anyone there?

---

### Post by bigken on 2006-10-05
what is your video card ?

---

### Post by werty on 2006-10-05
Hi
I dont use one. I am having a 915gav intel mb.

Thanks

---

### Post by bigken on 2006-10-05
ok run the dpkg command again and select vesa as your driver then you will  have to look up Intel® [GMA 900]("http://www.intel.com/products/chipsets/gma900/index.htm") onboard graphics subsystem

---

### Post by werty on 2006-10-05
Hi
dkpg with vesa failed too. The same error 'couldnt open RGB_DB'

I almost installed XGL, it was working and when i rebooted X11 broke. Could it be tht i have to remove the files of XGL

Thanks

---

### Post by bigken on 2006-10-05
sorry cant help you anymore try googling the error :-k

---

