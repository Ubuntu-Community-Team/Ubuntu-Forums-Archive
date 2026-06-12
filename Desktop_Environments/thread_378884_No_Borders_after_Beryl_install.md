---
title: "No Borders after Beryl install"
date: 2007-03-07
forum: Desktop Environments
---

### Post by Kenja on 2007-03-07
I feel like such a fool after going through countless threads about this issue.  Never did I see this.

It seems by default the window borders were disabled when I installed.  I went into beryl settings manager and under the Visuals tab, just turned window decorations on.

I hope I'm not that dumb and this actually helps someone

---

### Post by HasratUSA on 2007-03-07
i have the same problem. i did what you said but to no avail.

---

### Post by Daniel Rehm on 2007-03-07
Haha, I just spent the last half hour wondering what I ever did to make emerald hate me so much!

I didn't realize windows decorations = window borders/themes.

So yes, you really *did *help someone else by posting this!

---

### Post by HasratUSA on 2007-03-07
Please disregard my previous post. I added some two lines to my xorg.conf. they are:
1. Option 	   "AddARGBGLXVisuals"
2. Option         "AllowGLXWithComposite" "True"
(Actually my Beryl mentor is ManiacMusician and I didn't follow his rules exactly lol)
Then I saved the file and restarted X. Still the borders didn't come up and hence I chose to follow Kenja's *nod* method and the borders are back! No more pressing Alt and left-mouse button to move a window!

Thanks to these two great hackers (ManiacMusician and Kenja) I can finally run Beryl exactly the way the pros run it! :)

---

