---
title: "Removing extra apps [Resolved]"
date: 2007-05-04
forum: Desktop Environments
---

### Post by rillip on 2007-05-04
I instaled the xubuntu-desktop package on my Kubuntu 6.06 directory.  I decided it wasn't for me and ran 

sudo apt-get remove --purge xubuntu-desktop

Only removed like, 36.9k?  I seem to recall the install was like 300 megs?  I'm still seeing a ton of xfce related or installed programs that I don't really want.  Is there any easy way to remove them, or do I have to manually go through and remove them all?

---

### Post by meng on 2007-05-04
[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

---

### Post by hikaricore on 2007-05-04
> **meng said:**
> [http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

My response would have been more like:

```
sudo aptitude remove xubuntu-desktop
```

---

### Post by meng on 2007-05-04
Only that if you install with apt-get, then uninstalling with aptitude won't remove orphaned dependencies.
You have to install AND uninstall with aptitude in order for that trick to work.
And, AFAIK, apt-get autoremove won't work with 6.06
But, I'm happy to be proven wrong!

---

### Post by aysiu on 2007-05-04
> **meng said:**
> Only that if you install with apt-get, then uninstalling with aptitude won't remove orphaned dependencies.
You have to install AND uninstall with aptitude in order for that trick to work.
And, AFAIK, apt-get autoremove won't work with 6.06
But, I'm happy to be proven wrong!
You're correct on all counts, meng.

---

### Post by RTrev on 2007-05-04
> **meng said:**
> Only that if you install with apt-get, then uninstalling with aptitude won't remove orphaned dependencies.
You have to install AND uninstall with aptitude in order for that trick to work.
And, AFAIK, apt-get autoremove won't work with 6.06
But, I'm happy to be proven wrong!

If you do a search in Synaptic, you should find something under the search term "orphan"; [COLOR="Red"]gtkorphan[/COLOR].  It ends up as a selection under your System | Administration menu.  There appears to also be one specifically for KDE.. but I forget the name.

Seems (I haven't tested it much) to locate the libs with no dependencies on them.  Of course once you remove those, it brings up a new list of the ones which *now* have no dependencies given the ones just removed.  I had to run it 5 or 6 times to find all the (hopefully) old and unused junk.  

I think in my case it was because I'm running 64-bit and tried Automatix to get a 32-bit Swiftfox with all the plugins and so forth.  When I later removed most of this stuff, it seems that Automatix left some residue behind.

Hope this helps.

---

### Post by rillip on 2007-05-05
> **meng said:**
> [http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

This worked great, save for a few settings on default apps and such for some file types, I'll play with those and everything will be back to normal.  Thanks a ton!

Edit: actually, I just needed to restart the program that was doing it and it picked up on the default application the OS was selecting

---

