---
title: "How I repaired my html thumbnails"
date: 2009-08-12
forum: Desktop Environments
---

### Post by debernardis on 2009-08-12
Since in my Jaunty (very hacked) install I realized I hadn't thumbnails of html files (nor I could remind if I had those the time I upgraded from Intrepid or even before) I started looking at this issue.

It wasn't too difficult. I had some hint from [http://eazely.com/archives/tinker/803](http://eazely.com/archives/tinker/803) even if the guy who wrote that couldn't solve his problem.

Well, if you also lack them, just fire gconf-editor and search the key named **"desktop/gnome/thumbnailers/text@html"**.
I found that its command started with **"gnome-web-photo"** yadda yadda yadda thus omitting the path to the executable. Changing it into **"/usr/bin/gnome-web-photo"** was enough.

Then, "killall nautilus" or better restart the gnome session. Done :)

---

