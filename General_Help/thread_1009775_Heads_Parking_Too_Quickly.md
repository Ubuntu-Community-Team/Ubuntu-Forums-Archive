---
title: "Heads Parking Too Quickly?"
date: 2008-12-13
forum: General Help
---

### Post by anotherdisciple on 2008-12-13
I haven't tested it since hardy... and I'm running Intrepid now, but I don't believe that I'm part of the load cycle bug problem. My laptop seemed to be doing normal.

However, ever since I started using intrepid... every once in a while I hear what sounds to be the heads parking really hard. Does anyone else have this problem?

-Nick

PS- I have a Dell E1505 ... I can give you more info if need be.

---

### Post by anotherdisciple on 2008-12-16
...?

---

### Post by mykrob on 2008-12-16
This happens on mine too. Normally, when I get to my desktop, I run the command:

```

sudo hdparm -B 254 /dev/sda

```

and this stops it. This basically stops power management on the hard drive. I have noticed no ill effects. Some say this will reduce the available time when running on battery, but I have not noted any significant change in battery life or heat output.

When I don't put in this command, my load cycle count increases several times per minute. With the command entered, it seems to stop...


Hope this helps,
-myk

---

