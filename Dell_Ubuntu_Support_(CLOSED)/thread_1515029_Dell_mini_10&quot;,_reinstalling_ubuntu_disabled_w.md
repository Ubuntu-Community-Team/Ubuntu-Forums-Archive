---
title: "Dell mini 10&quot;, reinstalling ubuntu disabled wireless."
date: 2010-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Canucko on 2010-06-21
I let it auto-update to **10.04**, and that ruined the sound. So I reinstalled, making sure to use the netbook remix, and now out of nowhere my **wireless is disabled. **(sound is fixed at least).

I have tried the FN+2, and a couple other solutions; but nothing has worked. Since windows was never on this computer, it is not a windows related problem (as the help guide tried to tell me).

I use a dell mini-10", with 64 GB solid state HD, intel atom CPU. External CD drive.

Using commands I found that wireless was disabled, but in the notification area, it claims **"device not ready"**

---

### Post by mikewhatever on 2010-06-21
Starting from Karmic, Broadcom drivers are not loaded by default and must be enabled from System->Admin->Hardware-Drivers.
If you refer to guides and commands, at least provide links to the former and post the latter.

---

### Post by Canucko on 2010-06-21
Thank you, I am new to ubuntu.

I have now verified, that lan lines also do not work for it. Making your advice, not useful to me at this time.

I guess I'll try downloading something beyond the netbook remix on another computer, and installing that via CD rom.

---

### Post by mikewhatever on 2010-06-21
I have a dell inspiron mini 10 (1010), and both lan and wireless work, the latter after enabling the driver. Can you post the exact model of your Dell mini. In case you don't know, try [support.dell.com]("http://support.dell.com/support/downloads/index.aspx?c=us&l=en&s=gen"). You can use the service tag, which, in my case, is printed on the bottom of the netbook.

---

### Post by Canucko on 2010-06-21
I was mistaken, it is a 9". Inspiron Mini 9 (910). I imagine the driver should be the same one.

When I opened the Hardware Drivers, it attempted to search for drivers, then told me "No propietary drivers are in use on this system", giving me no options at all.

How did you enable your driver?

---

### Post by mikewhatever on 2010-06-21
Ubuntu installs everything from online repositories, including drivers. I just connected an ethernet cable and installed the bcmwl-kernel-source package, which is the same as using the Hardware Drivers utility.

---

### Post by ugm6hr on 2010-06-22
Confirm that wired ethernet does not work.

If so - post output from:
```
lshw -class network
```

---

