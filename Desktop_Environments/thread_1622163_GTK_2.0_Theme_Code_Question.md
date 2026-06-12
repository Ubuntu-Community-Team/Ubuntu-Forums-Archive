---
title: "GTK 2.0 Theme Code Question"
date: 2010-11-15
forum: Desktop Environments
---

### Post by substream on 2010-11-15
This is my first post, so hello all :)
I've been working with Ubuntu 10.10 for about a month now, and I'm in love, but I've been having a hell of a time trying to figure out this theme problem I'm having.

I installed the theme [Elegant GNOME]("http://gnome-look.org/content/show.php/Elegant+Gnome+Pack?content=127826") and all went smoothly, except the "handles" on the ends of NON-EXPANDED panels do not seem to be themed. You can see what I'm talking about in [this screenshot]("http://www.aww-kittah-aww.com/up/files/515/Handles2.png").

For the last few days, I've been tinkering with the code and the image files that make up the theme, and I finally found something interesting. It seems like the author didn't completely code the section of panel.rc (in the theme's folder) that deals with handles. In [this screenshot]("http://www.aww-kittah-aww.com/up/files/515/Handles3.png"), the left window contains the author's original code. As you can see, it does not even reference any images or attributes at all for the handles. The right window contains some code that I pulled from someone else's panel.rc file and pasted in to complete the code. Just for clarity, I also got into the theme's image folders and replaced "Panel/handle-h.png" and "Panel/handle-v.png" with solid red images, just so I could see where they appear on the screen when the new panel.rc is used. (When the old panel.rc is used, everything goes back to the way it looked in the [first screenshot]("http://www.aww-kittah-aww.com/up/files/515/Handles2.png"), even with the red handle images in place.)

As you can see, my red images DO replace handles, but only the handles that you would use to move things around inside the panels. The handles on the ENDS of the panels, however, remain unchanged. So is there another section of code I need to use to replace these? I'd like to make them completely transparent to complete this theme.

Thank you!

---

### Post by substream on 2010-11-19
No one? :-/
Bump

---

