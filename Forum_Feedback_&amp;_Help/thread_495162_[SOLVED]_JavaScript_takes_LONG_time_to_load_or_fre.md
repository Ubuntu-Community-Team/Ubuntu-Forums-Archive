---
title: "[SOLVED] JavaScript takes LONG time to load or freezes Firefox"
date: 2007-07-07
forum: Forum Feedback &amp; Help
---

### Post by altonbr on 2007-07-07
Before you start telling me it's my computer's hardware, please look at my signature for my specifications.

This has happened to me in Feisty and is happening to me in Gusty but now it actually GRAYS out Firefox because it's not responding. I have already reported the problem to Launchpad because the gray actually stays when Firefox begins responding again.

I have no verified way of knowing it's your JavaScript, but I though it was your Google Analytics code at one point. I'm a web developer, so I'm not one to jump to conclusions on this.

I was hoping someone could merely look into this problem for me as I would highly appreciate it and (possibly) other too.

This error does not occur in Gnome's Epiphany Browser nor Mozilla's Gran Paradiso (Firefox 3). I haven't researched their JavaScript rendering engines yet...

---

### Post by Vajra Vrtti on 2007-07-08
If you have extensions installed in Firefox, disable them all and then enable and test them one by one.

---

### Post by altonbr on 2007-07-09
No extensions.

---

### Post by ubuntu-geek on 2007-07-10
I cant seem to reproduce it.

---

### Post by altonbr on 2007-07-10
What's a simple program so I can record my desktop?

---

### Post by altonbr on 2007-07-11
JavaScript console report:

```
Error: uncaught exception: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIStringBundle.GetStringFromName]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://browser/content/browser.js :: anonymous :: line 3890"  data: no]

Warning: Expected end of value for property but found 'font-weight'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-91ffab3b-00074.css
Line: 1961

Error: $ is not defined
Source File: http://ubuntuforums.org/
Line: 1057
```

---

### Post by ubuntu-geek on 2007-07-11
> 
Error: uncaught exception: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIStringBundle.GetStringFromName]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://browser/content/browser.js :: anonymous :: line 3890"  data: no]


Appears to me you are missing this file? 
The other two errors would not cause any problems.

---

### Post by altonbr on 2007-07-11
Interesting, I backed up my ~/.mozilla/firefox folder and made Firefox create a new profile. Ubuntuforums.org now loads properly.

Sorry to waste your time.

Very interesting error though, I must say.

---

### Post by ubuntu-geek on 2007-07-12
No problem glad it was easily resolved.

---

