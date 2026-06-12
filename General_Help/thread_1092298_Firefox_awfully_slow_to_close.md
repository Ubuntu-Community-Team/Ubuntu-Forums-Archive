---
title: "Firefox awfully slow to close"
date: 2009-03-10
forum: General Help
---

### Post by Ingo88 on 2009-03-10
All too often Firefox takes (what feels like) forever to close.

1. You click the close button
2. It doesn't seem to respond
3. After a while the system tells you that Firefox isn't responding (see screenshot)
4. A few seconds later it finally closes

This sure is getting quite frustrating. What could be the problem? I use Firefox 3.0.7 in Ubuntu 8.04 (Hardy). I don't use any desktop effects and I have the following Add-ons installed:

DownloadHelper (disabled when I don't use it)
DownThemAll! (also disabled)
NoScript
Ubuntu Firefox Modifications

---

### Post by Peter09 on 2009-03-10
Firefox uses an awfull lot of disk, I find it slow to start and slow to close, it always seems very busy writing or reading from the HD when starting/stopping.

How full is your HD, if its getting full it could be slowing the process down.

---

### Post by philinux on 2009-03-10
Addons and themes can cause problems. First run firefox from a terminal to catch any errors.

From a terminal 

```
firefox
```

Then run firefox in safe mode to test the difference. 

```
firefox -safe-mode
```

Post back any errors.

---

### Post by Ingo88 on 2009-03-12
Thanks for your replies!

My disk is not getting full, so I don't think that's the problem.

I tried to run Firefox from terminal for some time, and for some reason I found it working better when I did so :?

Eventually I got that not-responding-window, and here's the output of that session. Nothing special here I guess...

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
```

I could try to use Firefox in safe mode for some time if you think it's relevant, but I'd prefer not to as that would mean NoScript being disabled all the time.

Thanks in advance for your further replies! :)

---

