---
title: "Can't boot vista after installing linux"
date: 2009-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vasan on 2009-04-20
:( How to install both vista and linux??? after i installed sabayon i was not able to boot vista. it saying bootmgr is missing. please help me..

---

### Post by meierfra. on 2009-04-20
In order to get a clearer picture of your setup, I suggest to boot into  Sabayon and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  (use the code tags:#)

---

### Post by Nudzacysie on 2009-04-21
Did you install ubuntu onto your external or did you cram it in with the rest of the other stuff in your hard drive.

---

