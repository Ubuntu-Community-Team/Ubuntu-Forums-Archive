---
title: "Getting my music off my iPod."
date: 2006-02-25
forum: Desktop Environments
---

### Post by roostishaw on 2006-02-25
Hello,

How do I take the music off my iPod, while still retaining all of the things like the artist and title so I can use it with something like Rhythmbox?

Thanks!

---

### Post by Suzan on 2006-02-25
Try gtkpod. 

You can export your music with gtkpod, it works very well.

---

### Post by roostishaw on 2006-02-25
Can it not copy mp4?
If so, how?

Thanks!

---

### Post by Zeroangel on 2006-02-25
The upgraded version of Rhythmbox has ipod support.

[http://mighmos.org/packages.php](http://mighmos.org/packages.php)

First download and install the libgpod package from that site using dpkg, than try to install rhythmbox also using dpkg. There is another dependency in there somewhere, fortunately you'll be able to resolve it by 'apt-get'ing the other needed file.

---

### Post by JoshHendo on 2006-02-25
I don't have a ipod, though some friends do, and even on a mac they had trouble getting music off. They can get music on, though not off. I don't know if it is possible :/

---

### Post by aysiu on 2006-02-25
The artist and title actually live *in* the file as embedded tags (they're called ID3 tags). You can copy and paste the files straight from the iPod hard drive. You don't need a special application.

---

### Post by Wallakoala on 2006-02-25
[QUOTE=Zeroangel]The upgraded version of Rhythmbox has ipod support.

[http://mighmos.org/packages.php](http://mighmos.org/packages.php)

First download and install the libgpod package from that site using dpkg, than try to install rhythmbox also using dpkg. There is another dependency in there somewhere, fortunately you'll be able to resolve it by 'apt-get'ing the other needed file.[/QUOTE]

I have tried to install this upgraded version of rhythmbox...trust me. I am pretty sure you need the newest gnome.

---

### Post by Zeroangel on 2006-02-26
You mean, you couldn't actually get rhythmbox to work? or you just couldn't get it to work with IPODs?

I have successfully installed it, but only after failing at first and having to clean up some dependencies. I haven't actually tested with an ipod because I don't have one. I just assume it would work considering the libs are now installed and there is an icon that says 'ipod' in rhythmbox.

---

