---
title: "how can i find out what cam i have?"
date: 2009-05-25
forum: General Help
---

### Post by Deathslicer on 2009-05-25
well as my title says
"how can i find what cam i have?"
i just switched to ubuntu and i would like to know how i can get my cam working.
now ive read some tutorials but they all knew what cam they had.
i know ive got the acer aspire 5100.
Could anyone give me a hint or support?

---

### Post by jmszr on 2009-05-25
Deathslicer,

I don't know for a fact that this will show your cam (I don't have one myself) but it shows about everything else. In the terminal: Applications > Accessories > Terminal copy and paste:```
 lshw -html > ~/Desktop/hardware.html

```
It will show up on your Desktop - just click on it and hopefully it will show you your cam.

---

### Post by paradigm2 on 2009-05-25
```

lspci

```

or 

```

lsusb

```

should show it.

Good news:

I also have an Acer 5100 series (there are different specific models though) laptop and had success getting the webcam to work with Cheese by upgrading to the (unofficial development) 2.60.30 kernel.

[http://ubuntuforums.org/showthread.php?t=1130178](http://ubuntuforums.org/showthread.php?t=1130178)

In lsusb my webcam comes up as:

Bus 001 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller

and works perfect in 2.6.30 on Jaunty for me with Cheese. 

Good luck. :)

---

