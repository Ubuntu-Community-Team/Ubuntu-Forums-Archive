---
title: "Clutterflow only works as root"
date: 2011-04-07
forum: Desktop Environments
---

### Post by taidoka on 2011-04-07
Hi there,

since a couple of days my clutterflow preview doesn't work in nautillus-elementary any more.
First I thought it is because of an ubuntu update. But I'm not sure.
I have installed the latest version from am-monkeyd's ppa.
The strange thing is that it works when I start nautilus as root.
Any idea?

taidoka

Edit: Again me. After several trys I found the solution:  press ALT + F2, enter: *gconf-editor* and then navigate to *apps > nautilus > preferences* and enable 'show_clutter'.
Restart Nautilus (nautilus -q). 
That's it. That did the trick. But I still don't know how this setting was unchecked...

---

### Post by yo_bhan on 2011-04-27
same problem..
but not work on my ati hd5850, only nautilus terminal work for me..
anybody help? :confused:

---

### Post by gamepoint on 2011-05-03
yeah ma..thanks for the solution. u rocks

---

### Post by geazzy on 2011-05-10
> **taidoka said:**
> Hi there,

since a couple of days my clutterflow preview doesn't work in nautillus-elementary any more.
First I thought it is because of an ubuntu update. But I'm not sure.
I have installed the latest version from am-monkeyd's ppa.
The strange thing is that it works when I start nautilus as root.
Any idea?

taidoka

Edit: Again me. After several trys I found the solution:  press ALT + F2, enter: *gconf-editor* and then navigate to *apps > nautilus > preferences* and enable 'show_clutter'.
Restart Nautilus (nautilus -q). 
That's it. That did the trick. But I still don't know how this setting was unchecked...

thanks for this solutions...
its work for me :D

---

### Post by srisharan on 2011-05-24
Thanks,It solved my problem

---

### Post by mrbinitie on 2011-06-03
Parfait :o

---

### Post by HolyDonut on 2011-09-27
One more step helped me out:

In gconf-editor, I checked show_clutter and then I also set clutter_test to 0 (it was set to 1) then I did the nautilus -q command and clutterflow started working again.

---

