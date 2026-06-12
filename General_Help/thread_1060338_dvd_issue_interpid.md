---
title: "dvd issue interpid"
date: 2009-02-04
forum: General Help
---

### Post by metalmaniac248 on 2009-02-04
when i try and play dvds in intrepid it plays the little clip at the begining of Paramount or 20th century fox or whatever, then it says "failed to read from media" and i cant get any further, 

k9copy isnt playin nicely either



any ideas?

---

### Post by mb_webguy on 2009-02-04
Am I right in guessing you aren't using the Medibuntu repository?

To play encrypted DVDs (which includes most commercial DVDs), you need to install the libdvdcss2 package from the Medibuntu repository.  Follow [these instructions]("https://help.ubuntu.com/community/Medibuntu") to add the Medibuntu repository to your software sources and install the packages you need for playing media on your computer.

---

### Post by metalmaniac248 on 2009-02-04
well i can play dvds now ,

but im getting an error with k9copy 

> Unable to save bookmarks in /home/nick/.kde/share/apps/kfileplaces/bookmarks.xml. Reported error was: Insufficient permissions in target directory.. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

now there is plenty of space on my hard drive, and iv tried to change the output path but it crashes everytime i do

---

### Post by mb_webguy on 2009-02-04
Try these commands in the terminal:```
sudo chown -R nick:nick ~/.kde
sudo chmod -R 700 ~/.kde
```

---

### Post by theophiles on 2010-04-12
That worked for me, thanks mb_webguy.

---

