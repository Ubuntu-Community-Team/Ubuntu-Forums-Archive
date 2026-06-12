---
title: "&quot;Non-free packages with staus other than installed&quot;"
date: 2009-05-19
forum: General Help
---

### Post by jpoRS on 2009-05-19
So I have been playing around with [vrms]("http://ubuntuforums.org/showthread.php?t=335094&highlight=vrms"), and after pulling the plug on a few things I don't need, I noticed that there were still "Non-free packages with status other than installed on <computer name>".

I have a few questions, firstly what does that mean?  Something either is installed or not, so a status other than installed would be not installed, and thus shouldn't show up . . . right?  Furthermore how to I get rid of these things?  I already uremoved them!

As an aside I would also be interested to hear if there is a way to check if you really need something. Like I know I don't need the Tangerine Icon theme, but some of these listings are less obvious.

Thanks,
jim

---

### Post by coffeecat on 2009-05-19
I've never used vrms so I've never seen that message, but I guess it means that there are still deb packages for uninstalled applications in the apt cache. If you mark apps for removal in Synaptic, they are uninstalled but the deb package is left in the cache. You have to select 'mark for complete removal' for the deb package to be removed as well. Have a look in /var/cache/apt/archives. You'll probably find deb packages for some apps you have already uninstalled.

If you want to clean out the whole apt cache, open a terminal and:

```
sudo apt-get clean
```This is useful for freeing up disc space, but if you need to reinstall something, the deb package will have to be downloaded again.

I don't know about the next question. I've never worried about installed stuff that I don't need. Considering that a default install of Ubuntu only takes up about 2.2GB, I'm happy that it's not Vista which takes up about 15GB even before you install any useful apps.

---

### Post by jpoRS on 2009-05-19
I use apt-get remove && apt-get clean.  that should take care of that, right?

And it is 100% true that "space" isn't really an issue, I doing this more out of curiosity than out of necessity.

jim

---

