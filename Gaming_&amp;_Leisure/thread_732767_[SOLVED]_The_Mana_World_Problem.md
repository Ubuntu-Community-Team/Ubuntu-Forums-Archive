---
title: "[SOLVED] The Mana World Problem"
date: 2008-03-23
forum: Gaming &amp; Leisure
---

### Post by yizuman on 2008-03-23
Uh oh!

I have a problem, I think I accidentally checkmarked the option to turn on the opengl and when I closed it, it won't load anymore.

So is there a way to uncheck it somewhere?

I tried to do a complete uninstall using the synaptic Package Manager and reinstalled the game again. Still won't load the game.

Any help please?

Thanks

---

### Post by lloyd_b on 2008-03-23
> **yizuman said:**
> Uh oh!

I have a problem, I think I accidentally checkmarked the option to turn on the opengl and when I closed it, it won't load anymore.

So is there a way to uncheck it somewhere?

I tried to do a complete uninstall using the synaptic Package Manager and reinstalled the game again. Still won't load the game.

Any help please?

Thanks

The problem is in the game's config file (which the uninstall/reinstall wouldn't have touched).

The file is "~/.tmw/config.xml".  You can delete this file, and it will be recreated (with default values) the next time you start the game.  Alternately, you can edit the file, and look for the following line:
```
<option name="opengl" value="1"/>
```
Just change the "1" to "0", and save the file.

Lloyd B

---

### Post by yizuman on 2008-03-23
Many thanks! That solved it!

---

