---
title: "runing google earth"
date: 2010-08-30
forum: Desktop Environments
---

### Post by manishdhr on 2010-08-30
hello, i am using ubuntu 10.04, but i am having problem in running Gearth
 this is what happens when i run google earth

[http://i556.photobucket.com/albums/ss4/manish_dhruw/Screenshot.png](http://i556.photobucket.com/albums/ss4/manish_dhruw/Screenshot.png)

similar problem occures with screensaver antspotlight

my graphics card is "via s3g unichrome pro"
i am newbie to ubuntu:confused:

plz help, thanx,

---

### Post by soldier1st on 2010-08-30
did you go to system/administration and select hardware drivers? also does it only happen in google earth?

---

### Post by manishdhr on 2010-08-30
yeah it also happens when i use screensaver antspotlight , dont know about games cuz i havent played any game on it yet

---

### Post by akoskm on 2010-08-30
Have you installed the appropriate drivers for your video card, like soldier1st [described]("http://ubuntuforums.org/showpost.php?p=9783872&postcount=2")?
What is your system specification?

---

### Post by nick_goodfate on 2010-08-30
Also if you have effects enabled try to disable them ...

---

### Post by majidromeo on 2010-08-30
Go to Google home page now search there Google earth now download and then install it.

---

### Post by akoskm on 2010-08-30
> **majidromeo said:**
> Go to Google home page now search there Google earth now download and then install it.

This thread isn't about installing Google Earth, see the first post.

---

### Post by manishdhr on 2010-08-31
> **akoskm said:**
> Have you installed the appropriate drivers for your video card, like soldier1st [described]("http://ubuntuforums.org/showpost.php?p=9783872&postcount=2")?
What is your system specification?

my pc's spec are-intel p4, 3ghz, 512 ram ddr2,
and in system>administration>hardware it is blank and showing
" no prop.. drivers are in use on this system"

---

### Post by manishdhr on 2010-08-31
> **nick_goodfate said:**
> Also if you have effects enabled try to disable them ...

effects are already diabled

---

### Post by wojox on 2010-08-31
If you open your terminal and run this command what does it say?

```
lspci | grep VGA
```

---

### Post by manishdhr on 2010-08-31
> **wojox said:**
> If you open your terminal and run this command what does it say?

```
lspci | grep VGA
```


 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

---

### Post by manishdhr on 2010-09-02
thanx to all of you for your time , my problem is solved by simply downloading updates

---

### Post by akoskm on 2010-09-02
> **manishdhr said:**
> thanx to all of you for your time , my problem is solved by simply downloading updates

Great, don't forget to update regularly! :D

---

