---
title: "jaunty nvidia 96 dual monitor problem"
date: 2009-05-06
forum: General Help
---

### Post by z35 on 2009-05-06
I recently updated to 9.04 from 8.10. The xorg.conf from before works (in single monitor mode). When I enable the 2nd monitor with nvidia-settings, and apply, there are a few issues which are new to 9.04. I installed the latest binary driver from nvidia, 96.43.11, which did not resolve any of the issues. 

I figured I would ask if anybody has experienced this and found a resolution before I post a bug report. 

The default main panel (with the menus, etc), turns blank. Also, there seems to be a large white screen that fills the background extending to the next monitor (which might be the desktop window). If I move a window off of this white window, the background does not update, so I get the moving window tailing effect. There seems to be a problem with the panel. 
Along the top of this white windowish thing, there is an empty inactive panel (which might be why it went blank). If I apply the settings a second time (different resolution on the 2nd monitor), compiz seems to crash, X freezes or something similar. 

I have attached my xorg.conf to this post. ~/.xsession-errors contains nothing. It somewhat works with compiz disabled. The white screen goes away and the desktop is normal, but the non-interactive panel still exists.

---

### Post by cynicalcylon on 2009-05-06
I've been having a problem with my second monitor too, since upgrading to 9.04 - the only thing I can get to actually open in the second monitor now is the internet, everything else defaults to my main monitor, despite being 'opened' on the second screen.

---

