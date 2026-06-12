---
title: "mencoder produces skiptastic video"
date: 2005-12-14
forum: General Help
---

### Post by Burke on 2005-12-14
When I try to reencode a wmv as an avi with mencoder, The resulting file skips a lot. I noticed that when I am encoding the file, it seems to think that there are more identical frames than there really are. I'm pretty sure this is the problem. Is there any way to make mencoder less sensitive to similar frames? Here's what I'm typing to transcode:

mencoder lights.wmv -ovc lavc -oac lavc -o lights.avi

Any ideas?

---

