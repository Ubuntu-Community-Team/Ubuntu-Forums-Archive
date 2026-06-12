---
title: "xorg memory usage"
date: 2010-01-03
forum: Desktop Environments
---

### Post by mnml on 2010-01-03
Hi,
I would like to know why xorg uses so much memory. On the screen I have attached its using 572 meg. Basicaly thats the mem usage I get after running a game for a while(without compiz on).

I was wondering why it doesn't release the actual mem. (This is real memory being used and not as cache as you can see I ran 
echo 3 > /proc/sys/vm/drop_caches before the screen.)

Should I stop using gnome?

---

### Post by gsmanners on 2010-01-03
You use Chromium and Flash? I think that has a knack for leaking X memory. Firefox just leaks its own memory. :P

---

### Post by wimpelmeesje on 2010-01-24
> **gsmanners said:**
> You use Chromium and Flash? I think that has a knack for leaking X memory. Firefox just leaks its own memory. :P

I'm using both Chromium and Flash and seem to be having the mentioned problem. Xorg currently takes up 1.6Gb of memory...

Is there a known fix or workaround?

---

