---
title: "Conky - if_up problem"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by nobdy on 2008-04-20
Hello,

I've just installed Conky and I'm currently building my own config.
To display the network traffic, I wanted to display it either for eth0 or wlan0. I thought I could use ${if_up eth0} to check if eth0 is used, but it doesn't work.
I tried this:
${if_up eth0}eth0${endif}

output: ${if_up} eth0

any ideas?

---

### Post by Ardent Maverick on 2008-04-28
I had this same problem, it's because the version of Conky in Gutsy's repos doesn't yet have the ${if_up} function implemented.  After I upgraded to Hardy and installed Conky from there it worked fine.

---

