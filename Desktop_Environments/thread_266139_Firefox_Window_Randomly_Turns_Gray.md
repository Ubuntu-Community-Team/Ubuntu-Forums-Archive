---
title: "Firefox Window Randomly Turns Gray"
date: 2006-09-26
forum: Desktop Environments
---

### Post by srunni on 2006-09-26
I've noticed that after updating to Firefox 1.5.0.7 (or at least it started shortly after that), the Firefox window randomly turns gray for a few seconds, then reverts back to whatever it was showing before. This is starting to get really annoying, especially when I'm reading an article or something of that sort. Part of the problem is that if I've scrolled down, when the gray window goes away, I'm back at the top of the page. Another problem I've been noticing is that when I'm typing stuff into forms (like the one to post stuff here), there are sometimes lags. There are absolutely no problems when using Konqueror or Opera, so I know it has to be a Firefox problem. Any ideas?

---

### Post by srunni on 2006-09-27
Anyone? This is really starting to get on my nerves ](*,)

---

### Post by srunni on 2006-09-27
Please?

---

### Post by caimex on 2006-09-27
Can you post a screenshot of what it looks like?
(to take a screenshit press the Print Screen key above the insert key on a standard keyboard.)

---

### Post by srunni on 2006-09-29
I think I figured out the problem: I recently set up a slideshow as my wallpaper, and Firefox was going gray whenever the picture changed. However, in case that isn't it and I continue to have problems with Firefox, I have a screenshot that I can post here.

---

### Post by BitTorrentBuddha on 2006-09-29
That's just compiz's way of saying that the program isn't responding, if it gets a response it will come back into color. I don't think there's a way of changing whether or not it greys out. Turning off the slideshow background should fix it, if that's an option.

---

### Post by varchar255 on 2007-07-08
I have this problem on Feisty with Firefox 2.0.0.4. Like BitTorrentBuddha indicated, the problem seems related to Beryl/Compiz because when I turned Beryl off, the Firefox windows were fine.

---

### Post by srunni on 2007-07-08
I know about the Beryl/Compiz thing where the windows turn gray, but that's not what this issue was - in Beryl/Compiz, the windows is "dimmed", whereas the problem I was having was the entire webpage area turning solid gray.

---

### Post by varchar255 on 2007-07-09
> **srunni said:**
> I know about the Beryl/Compiz thing where the windows turn gray, but that's not what this issue was - in Beryl/Compiz, the windows is "dimmed", whereas the problem I was having was the entire webpage area turning solid gray.

Yes, same here. I'm also not talking about the Beryl "window not responding" feature, it's definitely something different and something wrong. In my case, the Firefox window (where the webpage should appear) is either gray, or sometimes is the page that I was previously on (i.e. it's like the page never refreshes) but even when I manually refresh, nothing changes. The tabs, address bar, menu, etc. all remain normal. In fact, the window title changes to match the new webpage so I know Firefox is still responding, I'm just not sure why the page itself doesn't show up. It also seems consistent on certain pages--for instance, if I type [http://en.wikipedia.org/wiki/GNOME_VFS](http://en.wikipedia.org/wiki/GNOME_VFS) into the address bar, I only see a gray window where the page should be.

I restarted X and even with Beryl on, the problem went away. I had been hibernating it about two days in a row so maybe this is yet another Beryl video card memory problem.

---

### Post by srunni on 2007-07-09
Hibernation definitely has issues, and combining that with Beryl probably caused some conflicts.

---

