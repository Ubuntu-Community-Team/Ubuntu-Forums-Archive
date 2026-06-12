---
title: "pavilion 3000 fn button"
date: 2009-05-23
forum: General Help
---

### Post by saias on 2009-05-23
I am an ubuntu 904 new user and I have some difficulties. My fn button doesnt work. Although it seems to be working (by showing graphic change on the contrast bar) it doesnt. I mainly want to change the contrast please help.

thank you.

---

### Post by wanchai on 2009-05-23
Have a look at
[https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard)

Maybe you'll find something similar to your model.

---

### Post by ithanium on 2009-05-23
i also have such a problem on my Sony Vaio FW series. The Fn button doesn't work. any help?

---

### Post by saias on 2009-05-23
no solution yet.Just to make it clear by giving an example. when i change the contrast by using the fn button, the contrast bar changes but the actual contrast of the display doesn't.

---

### Post by wanchai on 2009-05-24
I had the same problem on my laptop (HP6930) in Ubuntu 8.10, but it was fixed in 9.04. The fn buttons were recognized after editing the hal fdi file, but the brightness didn't change although the on screen display showed changing brightness. Brightness changes on AC connect/disconnect also didn't work.

The fix was to run the command
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
This at least fixed the function keys. If this works for you as well, put this line into a little shell script that gets run by the session manager whenever you log in.

In order to get back to the default mode, run the same command again, but replace "native" with "kernel".

---

### Post by saias on 2009-05-26
I got this error message:
```
X Error of failed request:  174
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  19
  Current serial number in output stream:  19
```
Any further suggestions?

---

### Post by nickdbliss on 2009-05-26
Do u use Propriety drivers or open drivers for graphics? When i use open drivers, those keys work. It changes brightness and all that but when i enable propriety drivers it doesnt work. Anyways i use open drivers though so not a problem. Thanks.

---

### Post by saias on 2009-05-26
I tried with the open drivers with same results. I switched back to the proprietary. Any other suggestions?

---

