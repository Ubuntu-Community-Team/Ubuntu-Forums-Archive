---
title: "Webcam and Mic drivers?"
date: 2009-03-16
forum: General Help
---

### Post by Miroku419 on 2009-03-16
Could anyone help me with gettin the webcam and mic drivers for the Toshiba Satellite A305-S6916.  Also, if you could give a tutorial on how to install everything correctly that would be nice.  Im a bit new to Ubuntu.

Thanks.

---

### Post by Crafty Kisses on 2009-03-16
Have you actually tried and see if the webcam even works? Try using Ekiga to see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings,(try both V4L and V4L2).

To test your webcam you can do this: There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the results of the following command:
```
lsusb
```

---

### Post by Miroku419 on 2009-03-16
> **Codename said:**
> Have you actually tried and see if the webcam even works? Try using Ekiga to see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings,(try both V4L and V4L2).

To test your webcam you can do this: There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the results of the following command:
```
lsusb
```

Yes I have tried...  But for some reason... On Ekiga it worked..

I guess there was a problem w/ the other ****... also my mic just needed to be boosted..

Thanks

---

### Post by Crafty Kisses on 2009-03-16
Alright cool man, if you want to take video or take a snapshot, there's a program called "Cheese" you can get it through the repos, I thought I'd tell you about it. 
```
sudo apt-get install cheese
```

---

### Post by lvleph on 2009-03-16
I would suggest getting easycam2. It is not in the repoes, but it is how I got my webcam working. Do a google search for it.

---

