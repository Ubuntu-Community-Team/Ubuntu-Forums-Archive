---
title: "Boot issue"
date: 2005-11-29
forum: Desktop Environments
---

### Post by andars on 2005-11-29
Two things, one isn't really a huge issue, its just kind of odd, the other is quite annoying on the other hand :P

1.  When booting it shows the Ubuntu bootsplash screen when I'm using Kubuntu (installed Kubuntu, not KDE ontop of Ubuntu).  

2.  It says in plain text uncompressing kernel....ok, then it goes on to the bootsplash screen and says Modules........ and half the time it sits there then goes back to the uncompressing kernel screen and just sits there doing nothing.

If someone could also post the default sources.list that would be awesome.

---

### Post by Xian on 2005-11-29
[QUOTE=andars]1.  When booting it shows the Ubuntu bootsplash screen when I'm using Kubuntu (installed Kubuntu, not KDE ontop of Ubununtu). [/QUOTE]

Check to see if the kubuntu-artwork-usplash pkg is installed.
If it is then issue this command:

$ sudo update-alternatives --config usplash-artwork.so

---

### Post by andars on 2005-11-30
I did not have that package installed, however after installing and setting it to default and rebooting, it still showed the Ubuntu usplash screen.

---

### Post by Xian on 2005-11-30
Did it not give you the option of selecting the Kubuntu splash?

```
$ sudo update-alternatives --config usplash-artwork.so
Password:

There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/kubuntu-splash.so

Press enter to keep the default[*], or type selection number:
```

---

### Post by andars on 2005-11-30
Yea it did, I set it to number two and rebooted and it still showed the Ubuntu usplash.

---

### Post by Xian on 2005-11-30
Well, I suppose you could experiment by renaming usplash-default.so and see if it reverts to the Kubuntu splash. If it doesn't, or if it doesn't load any splash then just rename the file back and back to square one.

---

