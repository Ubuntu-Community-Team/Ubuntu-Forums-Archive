---
title: "KDE 4.4 Web Slice Widget"
date: 2010-02-13
forum: Desktop Environments
---

### Post by lovinglinux on 2010-02-13
It looks like an awesome idea, but it doesn't work for me, only shows the loading animation. Does it work for you?

---

### Post by lovinglinux on 2010-02-14
bump

---

### Post by mionescu on 2010-02-14
It does the same thing to me as well. Weird.

---

### Post by wojox on 2010-02-15
Got it working somewhat. It's better as a desktop widget than taskbar.

Right click to choose settings and add as URL:

```
http://news.google.com/news/section?pz=1&cf=all&ned=us&topic=t&ict=ln
```

And Element to show:

```
#top-stories
```

That's about the best I could come up with so far. ;)

---

### Post by lovinglinux on 2010-02-15
> **wojox said:**
> Got it working somewhat. It's better as a desktop widget than taskbar.

Right click to choose settings and add as URL:

```
http://news.google.com/news/section?pz=1&cf=all&ned=us&topic=t&ict=ln
```

And Element to show:

```
#top-stories
```

That's about the best I could come up with so far. ;)

Thanks. That worked. I guess the problem is that the widget somehow wasn't able to read the content form the site I was testing.

Unfortunately, the content is bleeding from the widget. See attached pic.

---

### Post by wojox on 2010-02-15
Oh yeah I forgot about that. Same problem here. When I use the taskbar widget I can only see the top one inch of it. Couldn't move it either.

---

### Post by lovinglinux on 2010-02-15
I just created a thread to share web slice configuration. Take a look [here](http://ubuntuforums.org/showthread.php?t=1407352).

---

### Post by wojox on 2010-02-15
Cool, I'll dork around some more and add to that thread. That looks better by the way.

---

### Post by lovinglinux on 2010-02-15
> **wojox said:**
> Cool, I'll dork around some more and add to that thread. That looks better by the way.

I just figured it out. If it bleeds, just click the widget settings and click OK. When it refreshes, the content is adjusted.

---

### Post by lovinglinux on 2010-02-15
Anyone knows how to force links from web slices to open on the default browser instead of the widget itself?

---

