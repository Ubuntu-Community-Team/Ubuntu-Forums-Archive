---
title: "Rollup fails in GNOME 3 (Ubuntu 13.04)"
date: 2013-06-24
forum: Desktop Environments
---

### Post by deeck on 2013-06-24
I updated to Ubuntu 13.04 and installed GNOME 3 from PPA.
I noticed that the rollup feature doesnt't work, showing a black box under the shaded window.

Screen Shot:  [http://www.use.com/ed73b81a4046a8db6457](http://www.use.com/ed73b81a4046a8db6457)

Some advices to start solving the problem?
If you need more system specs, just tell me.
Thanks!

---

### Post by Frogs Hair on 2013-06-24
deeck, 

Please upload thumbnails via manage attachments  or use an image host url in consideration of users band width and monitor size

---

### Post by grahammechanical on 2013-06-24
There is something that I think we should confirm.
 
1) Did you install Ubuntu Gnome 13.04 and then put in the PPA for Gnome3. Or 

2) Did you install Ubuntu 13.04 and then put in the Gnome3 PPA? 

The first option is the one we should take. The second option will cause problems.

[http://ubuntugnome.org/](http://ubuntugnome.org/)

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

Regards.

---

### Post by markbl on 2013-06-25
> **grahammechanical said:**
> 
1) Did you install Ubuntu Gnome 13.04 and then put in the PPA for Gnome3. Or 

2) Did you install Ubuntu 13.04 and then put in the Gnome3 PPA? 

The first option is the one we should take. The second option will cause problems.
What problems? I've always done the second option, because it looks better (and note you also need an "apt-get install gnome-shell"). You essentially get the same result and it works fine.

---

### Post by deeck on 2013-07-01
Uploading the screenshot again.
The first option.
[IMG]https://chest.usm.cl/2013_06_24_355_ed73b81a4046a8db6457.jpg[/IMG]

---

### Post by PaulEdwards on 2013-07-08
I've been having this issue, too.
I upgraded from Ubuntu 12.10.

Is it possible to "Upgrade" from plain Ubuntu 13.04 to Ubuntu Gnome 13.04?

---

### Post by PaulEdwards on 2013-07-08
I discovered that this is a bug in Mutter which was fixed on May 15th and released in the 3.8.3 update on Jun 7th.
[https://bugzilla.gnome.org/show_bug.cgi?id=693714](https://bugzilla.gnome.org/show_bug.cgi?id=693714)

---

### Post by PaulEdwards on 2013-07-08
I've been using the GNOME3 Team PPA from Launchpad.net which currently offers Mutter 3.8.2:
[https://launchpad.net/~gnome3-team](https://launchpad.net/~gnome3-team)

I found that they have a Staging PPA which does offer Mutter 3.8.3 as well as newer versions of other components:
[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)

I added the repository and installed only the Mutter upgrade and it's associated required libraries, restarted mutter using the following command, and the Window Shade function is now working properly!
> mutter --replace &

This issue is resolved for me and I hope this information is helpful for others.

---

### Post by PaulEdwards on 2013-07-08
Ignore this message; can't delete it!

---

