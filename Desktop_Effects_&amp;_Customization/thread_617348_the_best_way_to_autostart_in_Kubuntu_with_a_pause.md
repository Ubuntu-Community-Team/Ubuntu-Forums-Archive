---
title: "the best way to autostart in Kubuntu with a pause"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by tribunal on 2007-11-19
Hi all!
I know a way to autostart Compiz-Fusion in Kubuntu.
Here it is:
a small script like this:
#!/bin/sh
sleep 20
compiz --replace &
kde-window-decorator --replace &

But there is a problem:
This script works fine for the first time, but later, after restarting KDE, compiz starts without any pause (cause it was among other apps and KDE remembered it)
So, compiz starts before some apps, like klipper, starts and I have problems
How can I add this "sleep 20"?

---

