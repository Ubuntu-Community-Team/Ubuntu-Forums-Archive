---
title: "Dell Inspiron 1420 N Gutsy No sound"
date: 2008-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by factor2 on 2008-05-31
Upgraded from 7.04 to Gutsy in dell Inspiron Laptop. Everything but the sound works. Anyone have any thoughts?

---

### Post by factor2 on 2008-05-31
OK, I trolled the Internets, and did a little apt-get install gnome-alsamixer. 

About 3 seconds later, I found that several channels in the Alsa Mixer were muted. I unmuted them, and all was good. 

You can probably do the same thing if you access 'alsamixer' in the command line.

---

### Post by mrynit on 2008-06-02
**[size="5"]THANK YOU[/size]**

you can look at the attached image to see how I fixed it.

[IMG]http://farm4.static.flickr.com/3086/2544924910_fbb284f03b_o.png[/IMG]

To fix right click on volume icon > open sound control > raise the level on PCM.

---

