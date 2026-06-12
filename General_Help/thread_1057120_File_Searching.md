---
title: "File Searching"
date: 2009-02-01
forum: General Help
---

### Post by Officer Dibble on 2009-02-01
I want to locate all the jpg images on my drive as there is a particular picture I am looking for... I have tried using the standard search feature using *.jpg but it doesn't find anything... what am I doing wrong, please?

How would you go about searching all your drives using a wildcard and extension, please?

---

### Post by taurus on 2009-02-01
Have you tried it from a terminal with the find command?

Applications -> Accessories -> Terminal
```
sudo find / -name *.jpg -print
```

---

### Post by Officer Dibble on 2009-02-01
I've just tried this suggestion, and it was very thorough thank you, but only on the one drive... and previewing the images using this method is going to be something of a nightmare... any other ways of doing this?


> **taurus said:**
> Have you tried it from a terminal with the find command?

Applications -> Accessories -> Terminal
```
sudo find / -name *.jpg -print
```

---

### Post by MarblePanther on 2009-02-01
You may like Picasa:

[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

You can use it to find *every* picture on your hard drive, including icons in obscure places.

---

### Post by taurus on 2009-02-01
> **Officer Dibble said:**
> I've just tried this suggestion, and it was very thorough thank you, but only on the one drive... and previewing the images using this method is going to be something of a nightmare... any other ways of doing this?

If you have other drives mounted, it will search through them too since the search starts at the root filesystem--/.

---

### Post by mb_webguy on 2009-02-01
Since Linux is case-sensitive, if your image is named "something.JPG", then the previously posted find command won't find it.  Try "sudo find / -name JPG" as well as the previous command.

---

### Post by adamlau on 2009-02-01
Install the catfish frontend to find/locate/slocate/tracker.

---

