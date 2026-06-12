---
title: "Where does FF keep Profile data in Ubuntu?"
date: 2006-09-25
forum: Desktop Environments
---

### Post by mjpatey on 2006-09-25
I've tried using the info at:

[http://www.mozilla.org/support/firefox/profile#backup](http://www.mozilla.org/support/firefox/profile#backup)

...but the path it gives in Linux for the Profile directory doesn't seem to exist on my machine:

> On Linux, the path is usually ~/.mozilla/firefox/xxxxxxxx.default/

I've tried to find this, but can find no directory called .mozilla, and no files whose extension is .default.

I'm trying to move my profile data to a shared partition used by both Ubuntu and Windows (for those times when I'm forced to boot into Win), so I have all my extensions, bookmarks, etc. accessible from both OSes.

Thanks for any help you may have in locating this directory!

-Mark

---

### Post by kidders on 2006-09-25
The location you referred to is correct. Firefox's user-specific settings are all stored in ~/.mozilla

---

### Post by mjpatey on 2006-09-25
Never mind.  Found it!  Somehow, I'm unable to find it using the "Search" feature.  Even after enabling hidden files/directories, it wouldn't show up in a search, for some reason.

I had to go to about:cache in Firefox, then use the path given, up to .mozilla/firefox, and go from there.

I wonder why it doesn't show up in a search?

---

### Post by kidders on 2006-09-25
That's odd. Mine shows up just fine when I search for it with something like **slocate -r "\.mozilla$"** or **find /home -name .mozilla**. I wonder what's going on :confused:

---

### Post by graigsmith on 2006-09-25
if your in nautilus, in your home folder, you can hit ctrl h, and it will show hidden files.  (all files with a dot infront are hidden)

---

### Post by CatKiller on 2006-09-25
> **graigsmith said:**
> if your in nautilus, in your home folder, you can hit ctrl h, and it will show hidden files.  (all files with a dot infront are hidden)

And files in the .hidden file, I discovered today. Which was exactly what I wanted. Hooray!

---

