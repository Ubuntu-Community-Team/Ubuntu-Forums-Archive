---
title: "nautilus and evince-thumbnail running amok"
date: 2008-12-04
forum: Desktop Environments
---

### Post by howcome on 2008-12-04
I recently installed 8.10 on my thinkpad X41. One reason for moving up from 8.04 was that I found nautilus to run amok sometimes, taking up 90%+ of cpu performance. Killing the nautilus process helped me through at times (e.g., when giving presentations), but I expected this "bug" to be fixed in 8.10. 

I still find this problem in 8.10: nautilus -- now along with evince-thumbnail -- takes off on its own sucking up all CPU. My guess is that it precomputes thumbnails representing files. I don't need this as I don't use nautilus to navigate in the file system. 

So, how can this behavior be turned off?

---

### Post by howcome on 2008-12-04
> **howcome said:**
> So, how can this behavior be turned off?

I think I found the solution. Using gconf-editor, this is the setting to edit:

  desktop/gnome/thumbnailers/disable_all

---

