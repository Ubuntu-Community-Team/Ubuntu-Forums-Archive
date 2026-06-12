---
title: "Formatted Hard Drive, GUI boot not available"
date: 2009-04-06
forum: General Help
---

### Post by Acid_1 on 2009-04-06
Not a big issue, just wondering what causes it. I had a /, /home, /home/adam/Music, /home/adam/Videos, /home/adam/Downloads, and /tmp partition. I used a liveCD for Gparted, shrunk /, and combined Music, Videos, Downloads, and tmp to my /home/adam partition, without erasing my /home/adam partition. I changed the /tmp permissions afterwards so I could boot, but I just can't get the splash startup, the one with the big UBUNTU logo and the progress bar. It goes back and forth several times, does a text boot, and brings me to the GUI login screen, all is normal. Just wondering how to fix it. Thanks :)

---

### Post by cariboo on 2009-04-06
You resized the partitions, so the uuid has changed, you probably need to reconfigure grub. Have a look at this [thread=224351]howto[/thread]. I've used it so many times, I can do it by memory. :)

Jim

---

### Post by Acid_1 on 2009-04-07
I did it through my install. It's funny cause that's the guide I used to always go for when I had boot issues. I didn't think of just reinstalling grub. Dur. Thanks :)

---

