---
title: "Problem with Synaptic Package Manager"
date: 2009-04-16
forum: General Help
---

### Post by Chilternburt on 2009-04-16
Actually the problem is with me using synaptic, i was trying to uninstall Songbird and then reinstall it, but i chose the completely remove option, which obviously removes the app from my machine and from Synaptic...
is there a way to re add it??

Thanks in advance...

---

### Post by _Purple_ on 2009-04-16
As far as I know, Songbird is not in the Ubuntu repos yet. You can download and install it from [this link](https://help.ubuntu.com/community/Songbird).

---

### Post by frodon on 2009-04-16
Just install it the same way you installed it, there's no reason why it shouldn't work again.

---

### Post by Tibuda on 2009-04-16
> **Chilternburt said:**
> Actually the problem is with me using synaptic, i was trying to uninstall Songbird and then reinstall it, but i chose the completely remove option, **which obviously removes the app** from my machine and **from Synaptic**...
is there a way to re add it??

Applications are not removed from Synaptic.

---

### Post by mcduck on 2009-04-16
> **danielrmt said:**
> Applications are not removed from Synaptic.

Applications available in configured repositories are not removed from Synaptic (or apt).

Applications installed from packages downloaded outside of the repositories, however, will be removed since after removing the package isn't available any more. (It's not in repositories, and apt surely can't figure out which web site you downloaded the package from and get it for you :D)

---

### Post by 3rdalbum on 2009-04-16
This begs the question: If it was already installed, why did you want to remove it and reinstall (presumably) the same version? That accomplishes nothing - programs do not get "wear and tear" from use.

If you're having troubles with Songbird, glitches and such that weren't there before (or the program crashes immediately on opening when it worked properly before), you may have some success in removing Songbird's user preferences file. I assume it would be in a hidden folder called ".songbird" inside your home directory. Delete this and Songbird will create a new, fresh preferences file and will probably start working again.

If you don't delete the preferences file but you just reinstall the program, it'll hit the same corrupted preferences file and crash or become glitchy.

---

