---
title: "Firefox misbehaving"
date: 2009-06-03
forum: General Help
---

### Post by thegreger on 2009-06-03
Today I noticed that my Firefox didn't act the way it should. All history is gone, as is the startup page (though it's still correctly set up in preferences, I only get a blank page when I start firefox) and the bookmarks. It seems as if "new" history isn't created, since I cannot go back when I've clicked on a link. Also, it doesn't remember previously used addresses, even if I entered one just a second ago. 
Oh, and if I go to a certain page (say, ubuntuforums.org), start a new tab and go to another page then the first adress (ubuntuforums.org) is still displayed in the address field. The new page is loaded, though.

It seems just as if Firefox can't access the path where it stores it's history and other settings, but that's a very un-qualified guess.

I'm running Firefox 3.0.10, and I've already tried reinstalling it through Synaptics and disabling all add-ons. The only thing I have been messing with prior to this problem appearing was trying to install the google earth .bin-file, and the C++ library V3 (lib64stdc++6).

Oh, and the only two errors I can find in my Firefox error console is
```
Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 764"  data: no]
```and
```
Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.10/components/nsBrowserGlue.js :: bg__initPlaces :: line 449"  data: no]
Source File: file:///usr/lib/firefox-3.0.10/components/nsBrowserGlue.js
Line: 449
```

---

### Post by thegreger on 2009-06-03
Also, I've just tried doing a complete removal of Firefox and then re-installing it. Still the same problem, but the web page that *ought* to come up when I start firefox has changed from my home page to [www.mozilla.com](www.mozilla.com), so I guess the complete removal did what it should.

---

### Post by lovinglinux on 2009-06-03
> **thegreger said:**
> Today I noticed that my Firefox didn't act the way it should. All history is gone, as is the startup page (though it's still correctly set up in preferences, I only get a blank page when I start firefox) and the bookmarks. It seems as if "new" history isn't created, since I cannot go back when I've clicked on a link. Also, it doesn't remember previously used addresses, even if I entered one just a second ago. 
Oh, and if I go to a certain page (say, ubuntuforums.org), start a new tab and go to another page then the first adress (ubuntuforums.org) is still displayed in the address field. The new page is loaded, though.

This is a common problem caused by a corruption in the file *places.sqlite* in your Firefox profile. For future reference, make regular backups of you profile with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) and restore the most recent backup to solve the problem. Alternatively, deleting the file *places.sqlite* would also fix the problem, then you would need to restore your bookmarks from Firefox bookmarks backups if you don't use FEBE.

---

### Post by thegreger on 2009-06-03
Thanks a lot, deleting the *places.sqlite* solved the problem!

---

