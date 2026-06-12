---
title: "Barnes and Noble Audio"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Sweezel on 2006-09-05
How do I get one of these songs to play?

[http://music.barnesandnoble.com/search/product.asp?z=y&EAN=054645159326&itm=5](http://music.barnesandnoble.com/search/product.asp?z=y&EAN=054645159326&itm=5)

I am at a loss...

---

### Post by meng on 2006-09-06
mplayer-plugin should do the trick in Firefox. Works for me. Check out the wiki on Restricted Formats too.

---

### Post by Sweezel on 2006-09-06
All I get is:
Totem could not play 'fd://0'.

I could not find mplayer-plugin in multiverse, but I did find mozilla-mplayer.

Any ideas? Do I need to move anything into the plugins folder?

---

### Post by llamakc on 2006-09-06
sudo apt-get remove  totem-gstreamer-firefox-plugin 

sudo apt-get install mozilla-mplayer 

Now you’re rockin’ with Dokken.

---

### Post by meng on 2006-09-06
> **Sweezel said:**
> I could not find mplayer-plugin in multiverse, but I did find mozilla-mplayer.
That's it. Check the wiki for more details.

---

### Post by Sweezel on 2006-09-06
> **llamakc said:**
> sudo apt-get remove  totem-gstreamer-firefox-plugin 

sudo apt-get install mozilla-mplayer 

Now you’re rockin’ with Dokken.



Don't come a knockin cause the house is now a'rockin!


Thanks!

---

