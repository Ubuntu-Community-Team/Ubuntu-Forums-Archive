---
title: "Black Screen in 12.04"
date: 2012-05-21
forum: Desktop Environments
---

### Post by Regrets1015 on 2012-05-21
[SIZE=3]I get a black screen after I try to log in to Ubuntu. 

I can see the cursor and move it around but it is all that shows after logging in. 

It happened after I installed the Nvidia graphics driver and rebooted.[/SIZE]

---

### Post by sammiev on 2012-05-21
> **Regrets1015 said:**
> [SIZE=3]I get a black screen after I try to log in to Ubuntu. 

I can see the cursor and move it around but it is all that shows after logging in. 

It happened after I installed the Nvidia graphics driver and rebooted.[/SIZE]

Reboot and try booting into recover mode.

---

### Post by wilee-nilee on 2012-05-21
> **Regrets1015 said:**
> [SIZE=3]I get a black screen after I try to log in to Ubuntu. 

I can see the cursor and move it around but it is all that shows after logging in. 

It happened after I installed the Nvidia graphics driver and rebooted.[/SIZE]

Use the safe graphics from the recovery. 

Did you look in the additional drivers for that nvidia driver?

---

### Post by Regrets1015 on 2012-05-21
> **wilee-nilee said:**
> Use the safe graphics from the recovery. 

Did you look in the additional drivers for that nvidia driver?

I installed the "Recommended" driver.

---

### Post by raja.genupula on 2012-05-21
post output of this 
```
lspci -nn | grep VGA
```

---

### Post by Regrets1015 on 2012-05-22
> **raja.genupula said:**
> post output of this 
```
lspci -nn | grep VGA
```

So I go to Boot Menu and select Ubuntu to boot up... then I get this area where I put in a command. 

Is that what you are talking about?

---

### Post by roellipsch on 2012-05-23
This work-around worked for me.

1. Be stubborn and still log-in
2. Wiggle with you keyboard and mouse untill you get a empty desktop
3. right mouse click -> Change Background Setting
4. In the new window select -> All Settings
5. Select Additional Drivers
6. Remove/disactivate NVidia driver
7. Reboot
8. Work from there to repair :)

Good luck

---

### Post by jadtech on 2012-05-23
> **roellipsch said:**
> This work-around worked for me.

1. Be stubborn and still log-in
2. Wiggle with you keyboard and mouse untill you get a empty desktop
3. right mouse click -> Change Background Setting
4. In the new window select -> All Settings
5. Select Additional Drivers
6. Remove/disactivate NVidia driver
7. Reboot
8. Work from there to repair :)

Good luck

hehe sounds like a winner to me if you cant lick it one way muscle your way through..

---

