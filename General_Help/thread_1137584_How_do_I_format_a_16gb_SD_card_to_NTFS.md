---
title: "How do I format a 16gb SD card to NTFS?"
date: 2009-04-25
forum: General Help
---

### Post by crispeto on 2009-04-25
I want to format my 16gb sd card to ntfs using my ubuntu machine. Is there a way? I'm pretty new so go slow:). Thanks.

---

### Post by dcstar on 2009-04-25
> **crispeto said:**
> I want to format my 16gb sd card to ntfs using my ubuntu machine. Is there a way? I'm pretty new so go slow:). Thanks.

Install the **gparted** (Partiton Manager) package.

---

### Post by crispeto on 2009-04-25
I tried that but the ntfs option is grayed out. Fat32 is ok but not ntfs. What am I doing wrong?

---

### Post by platinumriver on 2009-04-27
You need to install additional packages. First, close GParted.

Download the ntfsprogs package. 

```
sudo apt-get install ntfsprogs
```

Open GParted. You will see the option to format to NTFS. You can do the same thing for the other grayed out file systems.

If you want JFS support in GParted, install jfsutils.

```
sudo apt-get install jfsutils
```

Now JFS will show up as an option.

---

### Post by crispeto on 2009-04-27
Hey thanks! That worked! I now have a formatted SD card in NTFS. And sure enough it allowed me to transfer the whole backup. Thanks a ton!

---

### Post by platinumriver on 2009-04-27
Sure. No problem. Ubuntu has great support for NTFS now.

---

