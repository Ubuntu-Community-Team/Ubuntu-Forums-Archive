---
title: "gconftool-2 and setting background"
date: 2009-06-09
forum: Desktop Environments
---

### Post by Innova on 2009-06-09
I wrote a perl script that loops through my bg directory and randomly pics an image.  It then calls:

gconftool-2 --type=string --set /desktop/gnome/background/picture_filename /home/wesley/pics/bgs/$file

If I run the perl script from the command line it works fine.  When I put it in crontab, the background does not change.  I have verified that cron is working (I redirect the output, and the file gets created with the new background image listed).  This worked fine in 8.04.

Any idea why it wouldn't be working now?

---

### Post by Innova on 2009-06-17
No one knows why this script does not work from cron?

---

### Post by Innova on 2009-06-29
So I noticed that if I log out, and log back in, the background changes also.  However, it does not change "on the fly".

---

