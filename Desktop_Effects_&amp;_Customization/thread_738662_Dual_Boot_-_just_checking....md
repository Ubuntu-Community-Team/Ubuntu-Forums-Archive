---
title: "Dual Boot - just checking..."
date: 2008-03-28
forum: Desktop Effects &amp; Customization
---

### Post by zoomiest on 2008-03-28
Just need to confirm... 

When I install a Ubuntu desktop disk on an existing windows machine, and it sets up a new partition... all my windows apps will work okay?

I have a desktop machine I use for work, and its configured right. I would like to be using a linux desktop like I do at home, and I can - except for a few apps, so dual boot will work great for me.

Just wanted to confirm that everything makes it through the partitioning process...

---

### Post by kool_kat_os on 2008-03-28
all your apps will still work fine but before installing backup your HD

---

### Post by Lantesh on 2008-03-28
If the hard drive only has one partition right now (the one Windows is on) you first have to shrink that partition down.  You then have to create an ext3 partition in the resulting empty space for your Linux install, and a ext2 partition for your Linux swap file.  There is partitioning software on the Ubuntu live CD.  You can do it all from there, but you kind of have to understand partitioning to do it correctly.

---

### Post by Mehashi on 2008-03-31
My advice in your situation would be to use a wubi install on your windows system. This is how I tried Ubuntu before a true install. It worked no problems for me!
Essentially it seems to Install ubuntu on a virtual hard-drive so no worries about partitioning!

Check out [Wubi]("http://wubi-installer.org/") if you are interested!
Good luck!
^_^

---

