---
title: "New favicon missing?"
date: 2007-04-17
forum: Forum Feedback &amp; Help
---

### Post by mmcmonster on 2007-04-17
I love the new favicon that shows up next to the URL for the forum.  So much that I deleted my old link to the forum and created a new one to reload the favicon.

Unfortunately, it didn't work.  Can anyone reproduce this in firefox on WinXP or Ubuntu Fiesty?  Create a link in your bookmarks to [http://ubuntuforums.org/](http://ubuntuforums.org/).  I end up with a generic blank favicon in my bookmarks.** :-(**

---

### Post by Compyx on 2007-04-17
I usually notice that a new favicon only shows up in Firefox after visiting the page a second time. I have no idea why, but that's how it works on my box (probably something to do with the browser's cache).

---

### Post by mmcmonster on 2007-04-17
Yeah, except that in this case, I've been trying for the last few days to get it to load. :-(

Anyone able to reproduce my problem?  Or prove me wrong?

---

### Post by rajeev1204 on 2007-04-17
ya its a known bug .

Turns out , the favicon for ubuntuforums is 24 kb and firefox restricts this to 16 kb .So u get a blank favicon.

If the forum admins are listening , can we have the favicon below 16 kb? :D 


[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/102848](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/102848)


Interestingly its the same for ubuntu.com

---

### Post by olspookishmagus on 2007-07-17
I had the same problem with these forums as well, did a search and come to the solutions which, for the sake of continuity and history, I copy-post here.

So, alternatively of waiting for a favicon of lesser filesize, you can install [Favicon Picker 2](https://addons.mozilla.org/en-US/firefox/addon/3176) it's an extension that allows you to manually select favicons for your bookmarks. Use this to update these forums favicon to [this favicon](http://ubuntuforums.org/favicon.ico).

Thanks to **ImpelGD** for posting [this](http://ubuntuforums.org/showpost.php?p=2473732&postcount=3).

---

