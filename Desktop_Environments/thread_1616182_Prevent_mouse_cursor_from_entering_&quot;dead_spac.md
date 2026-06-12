---
title: "Prevent mouse cursor from entering &quot;dead space&quot; in dual monitor setup"
date: 2010-11-07
forum: Desktop Environments
---

### Post by jeff_themovie on 2010-11-07
Hi,

I've installed Maverick on my laptop (Thinkpad x201) and I have an external monitor attached. The laptop's screen is 1280x800 and my monitor is 1680x1050, and they are configured side-by-side, bottom aligned.

Since the two displays have different heights (vertical resolutions), there is a 250px tall space above my laptop display that is present in the virtual (combined) desktop. I don't mind that I can move windows into that area, but I'd prefer if my mouse cannot enter that space. Now when I throw my mouse cursor upward, instead of the cursor sticking to the top edge of the display, the cursor goes past the edge and into that hidden space (which makes accessing the main menu or other parts of the top panel unnecessarily slow).

Is there a setting I can change to prevent my mouse from entering that "dead space" above my display's edge?

**Update:** Looks like desktop icons are also placed in that area, making them inaccessible. Any way to prevent this is also appreciated.

Thanks,
Jeff

---

### Post by jeff_themovie on 2010-11-08
Further searching lead to this:

[http://brainstorm.ubuntu.com/idea/24412/](http://brainstorm.ubuntu.com/idea/24412/)

which had links to these

[https://bugs.launchpad.net/ubuntu/+source/libxrandr/+bug/373367](https://bugs.launchpad.net/ubuntu/+source/libxrandr/+bug/373367)
[https://bugs.freedesktop.org/show_bug.cgi?id=20334](https://bugs.freedesktop.org/show_bug.cgi?id=20334)

The Launchpad bug report also has a workaround program. I guess this won't be fixed anytime soon.

---

### Post by virtuousd on 2010-11-23
I have this very same problem, and it seems to be a pretty essential issue. The menu items on the side of the screen with the dead space are very difficult to press, since usually one relies on the collision with the screen edge to position the mouse over them.

The link from the second post fixes the problem, but in a very ugly and unreliable way. For instance, I have a laptop so I am only using dual screens in certain locations, and of different sizes and configurations. Thus I have to set up the workaround individually for each location, which is a pain.

---

