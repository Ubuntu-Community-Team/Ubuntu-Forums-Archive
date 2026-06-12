---
title: "changing firefox download action for .mp3 files?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by wwuster on 2006-09-05
When I click on a link like [http://podcast-files.cnet.com/podcast/cnet_podcast082306.mp3](http://podcast-files.cnet.com/podcast/cnet_podcast082306.mp3), firefox in Ubuntu opens it with mplayer plugin for mozilla. I'd rather that it open it with xmms, but I can't find where to change that setting. How do I do it?



thanks,

William

---

### Post by ayoli on 2006-09-05
go to menu edit > preferences, then pick downloads tab, then clik "view and edit actions"

---

### Post by wwuster on 2006-09-05
> **ayoli said:**
> go to menu edit > preferences, then pick downloads tab, then clik "view and edit actions"

I did that but the mp3 extension is not listed. There are about 6 other multimedia extensions listed and I can change those. But can't change .mp3 since it's not there.

thanks,
William

---

### Post by oofnik on 2006-09-06
I am trying to do the same thing, except for the DIVX file type (same MIME as AVI, which is listed). If anyone knows how to add a new file type in download actions, please help!

---

### Post by orb9220 on 2006-09-07
Try starting a thread entiled: Firefox adding,modifiny,deleting mime types.

That may click somone's memory.

---

### Post by mssever on 2006-09-07
I remember doing something in about:config along these lines but I can't seem to find what I did.

---

### Post by stlolth on 2007-09-12
This add-on should do the trick. [https://addons.mozilla.org/en-US/firefox/addon/4498](https://addons.mozilla.org/en-US/firefox/addon/4498)

---

### Post by mcduck on 2007-09-12
> **mssever said:**
> I remember doing something in about:config along these lines but I can't seem to find what I did.

type about:config in the address bar, find the key 'browser.download.hide_plugins_without_extensions' and toggle it's value to 'false'. After that you'll be able to see everything in Edit/Preferences/Content/File Types/Manage.

---

