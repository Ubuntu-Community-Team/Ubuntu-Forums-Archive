---
title: "&quot;Browse for file&quot; dialogs take forever to display contents"
date: 2012-05-19
forum: Desktop Environments
---

### Post by snowweb on 2012-05-19
I'm using Ubuntu 12.04LTS with the latest KDE desktop and I've noticed that whenever I click 'open' or 'save as' in any application it takes many minutes for the dialog to show the files. Often it just doesn't happen before I give up waiting (maybe after 10 minutes).

I suspected this might have something to do with mounts within fstab failing. I had a mount in there for mounting my NAS, but it's often switched off and will fail if that's the case. But why should an open file dialog try to do a 'mount -a' each time? Is there a setting somewhere so that I can stop it?

I even tried commenting out that line in fstab, but it's still happening. I'm convinced that it is connected to this because if the NAS is switched on, everything works fine.

Thanks.

---

### Post by Zorael on 2012-05-21
Well, if you feel advanced you could run the program through strace and see what it's waiting for. Unless you know how though, skip that.

Have you tried removing your Places bookmarks? I'm not sure what file they're saved in. Removing **~/.kde** completely seems a bit excessive.

Does it happen on other users? Just create a temporary one and try there.

---

