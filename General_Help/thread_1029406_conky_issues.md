---
title: "conky issues"
date: 2009-01-03
forum: General Help
---

### Post by weeman7007 on 2009-01-03
the fs functions such as {fs_size}, {fs_used} and {fs_free} are not at all accurate for my ubuntu partition. 

this is the section of my conky configuration file:

${color red}Linux Space ${hr 2}$color
Size: ${fs_size /}
Used: ${fs_used /}
Free: ${fs_free /}

${fs_bar /}

${color red}Windows Space ${hr 2}$color
Size: ${fs_size /media/Vista}
Used: ${fs_used /media/Vista}
Free: ${fs_free /media/Vista}

${fs_bar /media/Vista}

The information for my Vista partition is the exact same as it is in GParted.

The information for my Linux partition is not however. It shows up in conky as:

size: 261.97GiB
used: 85.32GiB
free: 163.35GiB

For a start I seem to have lost 13.3GiB randomly, but also none of the values are the same as they are in GParted, which shows them as being:

size: 266.15GiB
used: 89.35GiB
free: 176.80GiB

Can anyone tell me why this is, and also how to get conky to display the actual values?

Thanks in advance

---

### Post by kaivalagi on 2009-01-03
Might be worth posting on this thread

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

lots of conky enthusiasts hang out there

---

