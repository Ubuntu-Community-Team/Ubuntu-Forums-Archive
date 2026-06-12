---
title: "Ugly fonts...found no solution"
date: 2006-02-04
forum: Desktop Environments
---

### Post by duffydack on 2006-02-04
In Suse 10 and KDE 3.5 i can get it to use 96dpi and set up MS fonts and get firefox looking pretty decent with most sites and im happy, but no such luck with kubuntu.  for some reason the same set up just doesnt quite look as good.  Im thinkin maybe i should just setup fonts/sizes for use at 75dpi, but i need some suggestions.  Keep trying fonts but cant seem to find a sweet spot?

---

### Post by joselin on 2006-02-04
Try to follow this link: [http://ubuntuforums.org/showthread.php?t=91280&highlight=firefox+font]("http://ubuntuforums.org/showthread.php?t=91280&highlight=firefox+font")

Hope that can be usefull for you.

Regards.

---

### Post by Eazy© on 2006-02-04
[http://ubuntuforums.org/showthread.php?t=104871](http://ubuntuforums.org/showthread.php?t=104871)

I'm a Linux noob, but this is what I had to do to get Verdana fonts to work for me

Must clarify that uninstalled all other fonts besides verdana and tahoma in the contolpanel. Once I did that and rebooted, I reinstalled the other fonts I uninstalled.

Must clarify one more thing. I'm a bit drunk right now, so Its possible I'm misunderstund the question :P

---

### Post by Velvet Elvis on 2006-02-04
It might help if you could post a screenshot of the "ugly" fonts you're seeing right now.

Disable hinting unless you're on a laptop.  Make sure anti-aliasing is on and install mstcorefonts.

```
sudo apt-get install msttcorefonts
```

---

