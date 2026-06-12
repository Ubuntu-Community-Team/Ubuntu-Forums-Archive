---
title: "Wine wont allow sound"
date: 2006-09-04
forum: Desktop Environments
---

### Post by underworld288 on 2006-09-04
ok I have tried this serveral times with no luck, I open winecfg from the terminal then I click on the audio tab and winecfg dies. The only thing that I can find that might tell you what the problem is is when I look at the terminal after winecfg shuts down it says this...

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/underworld288/.kde/socket-underworld288.
can't create mcop directory

any help?
thanks

---

### Post by mgmiller on 2006-09-04
there is a problem with the winearts.drv.so which fails when trying to autodetect your sound.

Here is the fix.
first, open a terminal, & go to the directory:
```
cd /usr/lib/wine
```

Then, make a backup of the old file:
```
sudo cp winearts.drv.so winearts.drv.so.old
```

Then delete the original file:
```
sudo rm wilnearts.drv.so
```

The next time you run winecfg, the audio tab should open normally and allow you to change all its settings.

I have to say, that even after doing this, I still can't get sound to work in wine.  At least not with Quicken, which is the only windows app I try to run in wine that has sound.  

Good luck.

---

### Post by underworld288 on 2006-09-04
when I went to delete the file it told me there is no such file, so maybe that is my problem. but, anyway how do I fix this?

thanks

---

