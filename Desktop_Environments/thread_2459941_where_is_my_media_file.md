---
title: "where is my media file?"
date: 2021-03-29
forum: Desktop Environments
---

### Post by ortermagic on 2021-03-29
I have just downloaded ubuntu again after long absence.I am trying to connect to media using terminal only to find that media no longer exists can anyone explain what's up please.

---

### Post by ortermagic on 2021-03-29
I am trying to reinstall an xbox one system using terminal commands yet i get a no media present on command using this video tutorial

[https://www.youtube.com/watch?v=CTLOhi3tbEs](https://www.youtube.com/watch?v=CTLOhi3tbEs)

---

### Post by ActionParsnip on 2021-03-30
At what point do you get the no media present.? What time in the video please?

---

### Post by mikewhatever on 2021-03-30
Not very informative, but there isn't a file named "media" in Ubuntu. It also makes no sense trying to connect to a file.
You might want to clarify the problem, a lot.

---

### Post by grahammechanical on 2021-03-30
I have no intention of watching a 33 minute video but if I am guessing correctly, you want to use Ubuntu to create either a USB memory stick or a CD ROM with an Xbox operating system on it or an Xbox repair USB or CD ROM.

Please confirm that you have downloaded an Xbox OS image. If you have done that the image file, which in Linux is called an ISO image file, should be in the Ubuntu Downloads folder/directory. If the Xbox ISO image file is on a CD ROM provided by Microsoft then you will need to have the CD ROM installed in the CD drive. Then you can change directory to /media

```
cd /media
```

Then when you use the command

```
ls
```

you will see a list of files that are on the CD ROM. In Linux/ubuntu when we put a CD ROM or DVD or USB memory stick in the drive bay or USB port it gets mounted at /media.

Regards

---

### Post by TheFu on 2021-03-30
I don't understand the problem.
Please describe exactly what you are doing, what you expect to happen, and which release and other software is involved. 
if there is any streaming or networking access we need to have that described too, please.

I skimmed the video. I don't see any normal Linux commands used, so the issue will need to be handled by someone who knows the script(s) being used.  Good luck.

---

