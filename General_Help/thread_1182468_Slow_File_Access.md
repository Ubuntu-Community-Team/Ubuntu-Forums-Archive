---
title: "Slow File Access"
date: 2009-06-09
forum: General Help
---

### Post by dejay703 on 2009-06-09
I recently upgraded to 9.04 64, and around the same time, uninstalled the packaged firefox, installed adobe-flashplayer and reinstalled firefox.

I can't remember which of these steps caused it, but now I have very slow file access on certain occasions.  I've experienced all of the following (and I think their somehow related)

1) When I go to gmail, and try to attach a file, it takes about 1-2 mins for the popup to browse my folders.  Firefox freezes in the meantime
2) When I transfer files from my digital camera, file transfers intermittently start and stop... and overall go very slow
3) Adding mp3 files to Audacious is horrendously slow.

Any ideas what could be causing this, or how to go about debugging?  I don't have any network drives or anything like that.  Everything is running off the one HD on my computer.

---

### Post by bhaverkamp on 2009-06-09
I suggest checking out the logs to see if there are any messages. FYI there was no need to uninstall firefox to install flash.

I recommend using the log viewer gnome-system-log

---

### Post by dejay703 on 2009-06-09
Wow, I never knew there was this log!  I'm looking at the "messages", and there's a bunch of segfaults for audacious and npviewer (which I believe is something with firefox/flash).  Any ideas on what to do?  I tried doing browsing for an attachment on gmail, but no new messages showed up.

I know you don't *need* to uninstall firefox to get flash working, but I could not for the life of me get it going with the newest flash player (which I needed).  The only way I could get it going was to first uninstall.

Thanks for the quick response!

---

