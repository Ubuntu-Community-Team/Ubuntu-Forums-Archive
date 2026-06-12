---
title: "Applications Menu is stil slow on my Xubuntu 12.04 / Xfce 4.10"
date: 2012-07-26
forum: Desktop Environments
---

### Post by Subway User on 2012-07-26
Hello everyone,

my Xubuntu 12.04 is almost perfect if not for a detail which isn't dramatic but bugs me a bit.

The applications menu takes 3 seconds to open on a cold boot although this well known bug should be already taken care of in Xfce 4.10.

I'm on Xubuntu 12.04 with Xfce 4.10 installed from the Xubuntu dev ppa. But the bug is still there.

Could you believe this is the last (I swear to god, the last) problem on my list before I call this installation 'perfect'?

Any ideas?

Thanks in advance,

SU

---

### Post by brainwash on 2012-07-26
> **Subway User said:**
> The applications menu takes 3 seconds to open on a **cold boot** although this **well known bug** should be already taken care of in Xfce 4.10.
So I does take 3 seconds on the first launch and then it will show up instantly? Can you provide any bug report or similar regarding this issue?

---

### Post by Subway User on 2012-07-26
> **brainwash said:**
> So I does take 3 seconds on the first launch and then it will show up instantly? Can you provide any bug report or similar regarding this issue?

Yes, it takes a while only the first time I click on the 'Menu' icon. After that, it works the way it's supposed to, it pops up immediately.

How can I provide you with bug reports? Forgive me, I just searched the web regarding this issue and found out that everybody was happy to find it solved in 4.10. Since I am running 4.10 (I've upgraded from 4.8 ), I'm afraid mine must be an exception.

Thanks.

SU

---

### Post by LewisTM on 2012-07-26
It takes a while to show the menu because Xfce has to compile all of the entries and build the menu when first invoked. You could preload it but that would mean a longer boot/login time.

Something like this as a startup application could do the job (needs xdotool):
```
sh -c "sleep 5 && xfce4-popup-applicationsmenu && xdotool key Escape"

```

You could also just cleanup the menu, remove unwanted items, to speed it up. 

The [Classic Menu indicator]("http://ubuntuforums.org/showpost.php?p=11726806&postcount=14") provides an alternative menu. I'm sure it pops up faster and I'm also sure it will make your panels show up 3 seconds later after login ;)

Cheers!

---

