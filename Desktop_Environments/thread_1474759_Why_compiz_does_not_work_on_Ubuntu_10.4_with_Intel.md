---
title: "Why compiz does not work on Ubuntu 10.4 with Intel"
date: 2010-05-06
forum: Desktop Environments
---

### Post by nil.esh on 2010-05-06
I'm wondering why no one fix this issue. The Compiz only worked with Ubuntu 8.4 and after stopped working on 9.x](*,) The issue is still there. I have **[COLOR="Red"]Intel® 82845G Graphics Controller[/COLOR]** on my PC and was waiting for new Ubuntu 10.4 with hope that it might resolve the issue but I am really disappointed:sad: with the new release as well. 

So requesting Ubuntu experts to [COLOR="Navy"]**help me out Please**[/COLOR].

---

### Post by _0R10N on 2010-05-06
> **nil.esh said:**
> I'm wondering why no one fix this issue. The Compiz only worked with Ubuntu 8.4 and after stopped working on 9.x](*,) The issue is still there. I have **[COLOR="Red"]Intel® 82845G Graphics Controller[/COLOR]** on my PC and was waiting for new Ubuntu 10.4 with hope that it might resolve the issue but I am really disappointed:sad: with the new release as well. 

So requesting Ubuntu experts to [COLOR="Navy"]**help me out Please**[/COLOR].

I have an intel graphic card myself and I'd only experienced some issue the first time I installed karmic. After updating the system, I never had a problem again. So, my guess is that if you aren't able to get compiz to work properly, then there's must be something else messing around.

If you would like to get some help on this. You could start by posting the output of
```
lshw -C display
```

Kind regards!

I forgot to mention that I'm on Lucid now, and everything keeps on wheels so far!

---

### Post by cascade9 on 2010-05-06
The intel i845 chipset graphics appear to be havign some major issues right now. :( Hopefully they get fixed....

---

### Post by AlanR8 on 2010-05-06
I have Intel graphics on my Compaq mini and Compiz works fine on Lucid......

---

### Post by nil.esh on 2010-05-15
I believe only the problem with :( Intel® 82845G Graphics Controller, rest of the other chip-sets works fine.
Now I am losing my hope. Day by day this graphic controller getting old so possible no one care about it :roll:, after all its based on Ubuntu community.

---

### Post by AnonCat on 2010-05-15
The Intel® 82845G chipset is blacklisted in compiz.  Unfortunately, unlike earlier version of Ubuntu, the blacklist can't be worked around without having to resort to a hex editor.

---

### Post by nil.esh on 2010-05-26
So is there solution ?

---

### Post by SunnyRabbiera on 2010-05-26
> **nil.esh said:**
> So is there solution ?

Try installing KDE, maybe kwin will work.
I have a intel here, all is fine

---

