---
title: "ubuntuforums not displaying properly?"
date: 2008-03-03
forum: Forum Feedback &amp; Help
---

### Post by mooglinux on 2008-03-03
for some reason ubuntuforums does not display the background or most images in firefox for me. it seems to work on and off, but mostly off. im using the most recent version of firefox 2 out of the ubuntu repos, and mystefied why i am having this problem, because no other websites have any probelms at all! *confused* suggestions? or is this an ubuntuforums in general issue? anyone else have this problem?

---

### Post by LaRoza on 2008-03-03
Clear the cache, and reload.

---

### Post by mooglinux on 2008-03-03
hey it worked. so now im curious, how does clearing the cache fix this? and what causes it in the first place?

---

### Post by LaRoza on 2008-03-03
> **mooglinux said:**
> hey it worked. so now im curious, how does clearing the cache fix this? and what causes it in the first place?

When a browser (in general) loads a page, it downloads all the images, text, scripts, stylesheets, etc. In stores them in a temporary directory. Instead of reloading a page every time, it first checks to see if it already has it. 

This is why images load longer the first time you view them, because they are being downloaded. The next time, it is almost instant, because it is being reloaded from the cache.

Clearing the cache makes the browser reload the image, instead of trying to load it from the local cache.

---

### Post by mooglinux on 2008-03-03
so if it doesnt display then the file in the cache was overwritten by data from another site or otherwise unusable?

---

### Post by LaRoza on 2008-03-03
> **mooglinux said:**
> so if it doesnt display then the file in the cache was overwritten by data from another site or otherwise unusable?

I imagine.

You can view what is in your cache, in Firefox, it is:

```

~/.mozilla/firefox/vkuuxfit.default/Cache

```

---

### Post by p_quarles on 2008-03-03
> **LaRoza said:**
> I imagine.

You can view what is in your cache, in Firefox, it is:

```

~/.mozilla/firefox/vkuuxfit.default/Cache

```
Except that the name of the ****.default directory is randomly generated. It will be different for everyone. Use ```
ls .mozilla/firefox
``` to get the exact name.

---

### Post by LaRoza on 2008-03-04
> **p_quarles said:**
> Except that the name of the ****.default directory is randomly generated. It will be different for everyone.

Oh, I didn't know. (I just did a quick peek)

It is the only directory there for me, along with a couple files.

---

### Post by p_quarles on 2008-03-04
> **LaRoza said:**
> Oh, I didn't know. (I just did a quick peek)

It is the only directory there for me, along with a couple files.
Yeah, it's a quirk of Mozilla's products, which I know you don't use. It reflects the fact that they were originally designed to run on Windows.

---

