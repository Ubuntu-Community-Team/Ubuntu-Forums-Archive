---
title: "Compiz Error:"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by einherier on 2008-02-06
I followed this tutorial to try to get compiz working on my computer:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

I'm not using Feisty, im using Gutsy, but I figured it should work but when I try to run it, it doesnt seem to work..........I try to go to compiz config manager and nothing happens....

so i went to console and this is what i ended up with....any insight?
```

praetorian@praetorian-linux:~$ compiz
Checking for Xgl: X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  30
  Current serial number in output stream:  30
not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by FuturePilot on 2008-02-06
Did you add those repos to your sources.list? If you did you're going to need to remove them then completely purge anything related to Compiz and reinstall them from the Ubuntu repos. Also what is your graphics card?
Gutsy comes with Compiz Fusion by default.

---

### Post by einherier on 2008-02-06
> **FuturePilot said:**
> Did you add those repos to your sources.list? If you did you're going to need to remove them then completely purge anything related to Compiz and reinstall them from the Ubuntu repos. Also what is your graphics card?
Gutsy comes with Compiz Fusion by default.

ahh...pain in the butt...i did add those repos....

I am using restricted driver ATI accelerated graphics driver.... I don't know how to pull up additional information about it.

---

### Post by einherier on 2008-02-06
Crap:

```

praetorian@praetorian-linux:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

---

### Post by FuturePilot on 2008-02-06
What is the output of 
```
lspci | grep VGA
```
This will display your graphics card. Most likely you need to install XGL.

---

### Post by einherier on 2008-02-07
```

praetorian@praetorian-linux:~$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
praetorian@praetorian-linux:~$ #You mean I might not have to buy new hardware?
praetorian@praetorian-linux:~$ 


```

---

### Post by FuturePilot on 2008-02-07
Yes, try installing XGL
```
sudo apt-get install xserver-xgl
```
Log out and then back in for it to set itself up.

---

