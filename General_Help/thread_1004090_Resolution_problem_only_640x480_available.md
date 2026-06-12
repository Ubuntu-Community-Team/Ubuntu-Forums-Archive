---
title: "Resolution problem: only 640x480 available"
date: 2008-12-06
forum: General Help
---

### Post by pointfive on 2008-12-06
I just installed Ubuntu on an old Dell (P4 2.8Gz). I had to use "Safe Graphics Mode" to do so. It looks like everything is working fine, except the only resolution I can select is 640x480. (XP was able to run 1024 on this machine without a problem.)

Here's what lspci shows the graphics card to be: 

```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

How might I go about installing a video driver that will allow for higher resolutions?

Thanks.

---

### Post by f37u5g0d on 2008-12-06
Go to System -> Preferences -> Main Menu.  Under "other" should be "Screens and Graphics."  Go ahead and add it.  Then go to Apps -> Other -> Screens and Graphics and you should be able to add screen resolutions there.

---

### Post by pointfive on 2008-12-07
Thanks. Between your advice, and a tutorial in [this thread]("http://ubuntuforums.org/showthread.php?p=3928636"), I was able to choose a different driver and resolution.

Much appreciated!

---

