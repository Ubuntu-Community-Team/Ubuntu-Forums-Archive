---
title: "What software is this?"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by ch_123 on 2007-12-22
I've seen this in a few distros, but I have never been able to find its name - the thing that shows system information on the desktop. Here's a good pic of it

[http://upload.wikimedia.org/wikipedia/en/3/33/Dreamlinux_screenshot.jpg](http://upload.wikimedia.org/wikipedia/en/3/33/Dreamlinux_screenshot.jpg)

Can anyone tell me what its called?

---

### Post by Ub1476 on 2007-12-22
It's Conky.

And it's in the repos.

```
sudo apt-get install conky
```
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

To edit conky write:

```
gedit ./concyrc
```

[Here's]("http://ubuntuforums.org/showthread.php?t=281865&highlight=post+your+conky") a nice thread.

---

### Post by ch_123 on 2007-12-22
Thanks mate :D

---

