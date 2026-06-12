---
title: "xulrunner causing firefox to crash"
date: 2009-05-13
forum: General Help
---

### Post by screaminfakah on 2009-05-13
Hello,
I did a fresh install of Jaunty and after all of my updates I ran firefox.  I installed adobe flash because videos wouldn't play and then it asked me to install missing plugins when I went to view a video so I installed swfdec.  I realized later these were conflicting so I uninstalled the adobe.
I was able to get the flash media to stream but I am experiencing alot of strange things in Firfox now.
When I open firefox it lags and in Firefox's error console it shows that xulrunner is creating multiple errors.  I went and reinstalled xulrunner but still have multiple problems with Firefox.  Also my bookmarks do not work and when I go to view my add-ons it crashes firefox.

Is there anyway to restore firefox to its orginal default settings with the default plugins/extensions?  I searched and have not found a definitive answer.
Thanks much.

---

### Post by lovinglinux on 2009-05-13
Start firefox in safe mode and disable the plugins.

```
firefox -safe-mode
```

I would recommend installing the adobe package and removing swfdec.

```
sudo apt-get remove swfdec-mozilla
```
```

sudo apt-get install flashplugin-installer
```

---

### Post by screaminfakah on 2009-05-13
Thanks for the reply.

Do you think that the add-ons could cause xulrunner to malfunction?  I am not real familiar with xulrunner, is it something just for the Firefox browser?

---

### Post by lovinglinux on 2009-05-13
> **screaminfakah said:**
> Thanks for the reply.

Do you think that the add-ons could cause xulrunner to malfunction?  I am not real familiar with xulrunner, is it something just for the Firefox browser?

[http://en.wikipedia.org/wiki/Xulrunner](http://en.wikipedia.org/wiki/Xulrunner)

---

### Post by screaminfakah on 2009-05-15
Didn't work.  I went into safe mode and reset everything & Still get the same errors.  Says something like "xpcom failed to load".
Im stumped.  Maybe I have a bad install?

---

### Post by screaminfakah on 2009-05-16
Solved!

Somehow my partitions were all screwed up when Ubuntu installed so I ran out of room!  I went in with the live CD and fixed the partitions then had to fix the my Grub boot loader and now I think I am ok.

Thanks for the help.

---

