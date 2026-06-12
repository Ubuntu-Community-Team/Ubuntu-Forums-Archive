---
title: "Unable to post in Ubuntu forums / Wordpress using Swiftfox"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Karbonik on 2006-08-30
I'm posting this question thru Epiphany, as under Swiftfox I suddenly lost the ability to type in the main field box both here in Ubuntu forums, and also in Wordpress blog.

I'm not a programmer, but would this have anything to do with php?

I seem to get problems in Swiftfox when I try to open .php pages sometimes.  Not all the time - I haven't figured out a pattern yet.

Any ideas?

---

### Post by skymt on 2006-08-30
Let's use the process of elimination. Does it work in Firefox? If it doesn't, I suspect a plugin conflict or configuration error. In that case, you should back up your bookmarks and rebuild your profile. If Firefox is fine 'n' dandy, Swiftfox is the problem. That would be hard to debug.

---

### Post by Karbonik on 2006-08-31
Nope - doesn't work in Firefox - I'll try the thing with backing up the bookmarks - extenions should be easy because I always save them to disk first.

My main concern is the passwords, tho.  They are a real pain to rebuild every time.

Speaking of, an entirely different issue is that for some reason my login to Ubuntu Forums never gets saved...

---

### Post by Karbonik on 2006-08-31
I just thought of another thing that could possibly be affecting it - A few days ago I attempted to use kflickr, which tries to open a page in the browser having the extension  " .auth" which kept attempting to open a page using the mplayer plugin.  I then went into the file association and made an entry for .auth for Swiftfox, Firefox, and Konqueror, in that order.  I have since removed it, tho.

---

### Post by Karbonik on 2006-08-31
Plugins:

SPL  - SPL file - Shockwave Flash
QTL - QTL file - Quicktime plugin 6.0
AVI - MS Video (AVI) - Kaffeine Starter Plugin
WM - WM file - Windows Media Player Plugin  (huh? did I accidentally transfer this from copying stuff from my windows build profile?)
WVX - WVX file - Windows Media Player Plugin
OGG - Ogg multimedia - mplayerplug-in 3.17
FLI - FLI file - mplayerplug-in 3.17 (this could be the Flickr file, no?)

---

### Post by Karbonik on 2006-08-31
OK - This post is done under Firefox.  

Moved out my entire .mozilla file from the /home/~/ , and started a new profile.
Difference in File association for plugins with a new profile is that 
AVI and OGG are not there.

Going to restore the previous profile, remove those Plugins, and attempt again.

---

### Post by Karbonik on 2006-08-31
Restoring the previous profile and changing/removing the mplayer plugins had no effect.

The configuration conflict apparently is elsewhere.

---

