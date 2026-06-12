---
title: "fullcircle ogg podcast rss feed cant be added to rhythmbox"
date: 2010-10-29
forum: Full Circle Magazine
---

### Post by cor2y on 2010-10-29
Hi all i have been trying to add the rss ogg feed of the podcast to rhythmbox but i keep getting this error.
```
Unable to parse the feed contents
```
This is only for the ogg feed , the mp3 one works.
Ubuntu Desktop 10.10 64bit, Rhythmbox 0.13.1, 
If its a rhythmbox problem anyone know a fix?
Yes the mp3 works but i would prefer ogg.

---

### Post by RobinC@Amethyst on 2010-11-01
> **cor2y said:**
> Hi all i have been trying to add the rss ogg feed of the podcast to rhythmbox but i keep getting this error.
```
Unable to parse the feed contents
```
This is only for the ogg feed , the mp3 one works.
Ubuntu Desktop 10.10 64bit, Rhythmbox 0.13.1, 
If its a rhythmbox problem anyone know a fix?
Yes the mp3 works but i would prefer ogg.

Hm. I get the same thing, more precisely:
```
There was a problem adding this podcast: Unable to parse the feed contents.
Please verify the URL: http://fullcirclemagazine.org/category/podcast/feed/atom/. 
Would you like to add the podcast feed anyway?
```

Will take a look into this one. Thks **RC**

---

### Post by RobinC@Amethyst on 2011-01-14
Better late than not at all...

I've tried around a dozen atom feeds in Rhythmbox now and every time I get:

> There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://anywhere.com/feed/atom](http://anywhere.com/feed/atom). Would you like to add the podcast feed anyway?

If 'yes' it lists the feed but you feeds nothing.

Just looking at the headers in the rss vs atom feed file, there are small but significant differences hence the parsing error. I'm guessing Rhythmbox' xml parser isn't configured for atom, but I haven't found anything to say that. I may go out this to the developers.. **RC**

---

