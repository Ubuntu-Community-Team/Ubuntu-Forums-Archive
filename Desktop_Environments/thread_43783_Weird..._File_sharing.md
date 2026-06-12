---
title: "Weird... File sharing"
date: 2005-06-23
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-23
I was under the impression that Windows cannot read from an ext3 hard-drive. I had read that here among other places. My brother somehow got it to. I have a dual-boot WinXP/Linux both. My brother, on the network has a Linux box. He set up sharing on his computer. Now I can read his .ext3 drive from Windows and transfer files back and forth... Nuts!

---

### Post by desdinova on 2005-06-23
When you share files over a network, its filesystem independent - i.e the act of sharing it just offers up the files, it doesn't matter whether their ext3, fat32 or wax platter.

---

### Post by Takis on 2005-06-23
Well, if you really want, you could try [ext2fsd](http://sourceforge.net/projects/ext2fsd) - but the last time I played around with it, it made my Windows *[COLOR=Red]very unstable[/COLOR]*. It's a much better idea to have a common FAT partition, but you can try this if you like.

---

### Post by Dave_is_sexy on 2005-06-23
Yep. 'filesystem's not relevant over a network, cos one OS talks to another and tells it what to do. And it uses it's own drivers to do it.

I haven't tried ext2fsd but i have tried what's available at:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

and it's pretty nice. Be sure to read all the docs tho, cos it's not perfect

---

