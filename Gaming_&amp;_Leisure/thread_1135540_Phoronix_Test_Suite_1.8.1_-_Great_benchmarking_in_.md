---
title: "Phoronix Test Suite 1.8.1 - Great benchmarking in linux with GUI"
date: 2009-04-24
forum: Gaming &amp; Leisure
---

### Post by budluva04 on 2009-04-24
A few months back I posted a HOWTO on installing the new Phoronix Test Suite 1.8.0b2 that was still in beta and required a bit of mucking around to get working. Well it's been released (last week April 16, 2009) and now they have created a .deb for it, and they also have Debian/Ubuntu repo's for us, there is a version in the official Ubuntu repo's as of right now but its the older 1.6 with no GUI.

Download Page

[http://www.phoronix-test-suite.com/?k=downloads](http://www.phoronix-test-suite.com/?k=downloads)

or direct download
```

wget http://www.phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_1.8.1_all.deb
```

then

```
sudo dpkg -i phoronix-test-suite_1.8.1_all.deb
```

KEEP IT UP PHORONIX AND HAPPY BENCHMARKING!!!!

---

### Post by wingnux on 2009-04-24
And where is the menu entry for it?

---

### Post by Vadi on 2009-04-24
doesn't add one, you need to do alt+f2 "phoronix-test-suite gui" but get php-gtk first (linked on their downloads I think)

---

### Post by budluva04 on 2009-04-24
sorry, my menu entry was created in the howto i made, and when i installed the new .deb it overwrote my old install so i didn't have to re-install php-gtk or make a menu entry, you can look over my tutorial for the beta install instructions here...

[URL="http://ubuntuforums.org/showthread.php?t=1108731"]
http://ubuntuforums.org/showthread.php?t=1108731[/URL]

EDIT: ya i just went to their download site and you do still need to install PHP-GTK2 which is the same version 2.0.1 iirc that i wrote instructions for in my howto i linked to above. you need to apply a patch to compile it, but have no fear its all in the howto...

---

