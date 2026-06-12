---
title: "Firefox problem"
date: 2009-04-09
forum: General Help
---

### Post by toehead2 on 2009-04-09
Firefox 3.0.8 is acting buggy, when I open it, nothing is displayed, not my home page nothing. clicking on the home button gets me to default google page. I also noticed all my bookmarks are gone, and the back, forward, and refresh buttons are greyed out.Firefox was working fine earlier in the day when I last used it.
Selecting the error console provides the following:
Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.8/components/nsBrowserGlue.js :: bg__initPlaces :: line 449"  data: no]
Source File: file:///usr/lib/firefox-3.0.8/components/nsBrowserGlue.js
Line: 449

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]

I will add that I really don't have a lot of add-ons installed with Firefox, only a couple of themes ( I think ).

---

### Post by Wayne_V on 2009-04-09
Are you on a system with low memory ($ free)?

Are you short of disk space ($ df -h ~)?

Try starting with a clean config:

$ ps -efa | grep firefox
(make sure all firefox processes are gone)
$ mv .mozilla SAVE.mozilla

Now run firefox and it should start with a new config.

---

### Post by toehead2 on 2009-04-09
> **Wayne_V said:**
> Are you on a system with low memory ($ free)?

Are you short of disk space ($ df -h ~)?

Try starting with a clean config:

$ ps -efa | grep firefox
(make sure all firefox processes are gone)
$ mv .mozilla SAVE.mozilla

Now run firefox and it should start with a new config.

Thanks Wayne_V
That seems to have worked, however I still don't have my bookmarks and it didn't remember my passwords, is this because I started with a clean config?
I guess I can always manually add the sites to my bookmarks.

---

### Post by Wayne_V on 2009-04-09
Something obviously got trashed in your .mozilla folder.   Your bookmarks and passwords are in there -- don't remember where they are stored right off - you could do a google search on that and just try copying those files from SAVE.mozilla to .mozilla.

---

### Post by toehead2 on 2009-04-10
> **Wayne_V said:**
> Something obviously got trashed in your .mozilla folder.   Your bookmarks and passwords are in there -- don't remember where they are stored right off - you could do a google search on that and just try copying those files from SAVE.mozilla to .mozilla.

Did a google search and found several instances of this happening in Linux as well as Windows. This appears to be a bug. Hopefully the folks at Mozilla will provide a patch soon.
Thanks again for all your help, Wayne_V

---

### Post by kaibob on 2009-04-10
> **Wayne_V said:**
> Something obviously got trashed in your .mozilla folder.   Your bookmarks and passwords are in there -- don't remember where they are stored right off - you could do a google search on that and just try copying those files from SAVE.mozilla to .mozilla.
I believe the Firefox bookmarks are stored in the places.sqlite file. This file is in a subdirectory of the ~/.mozilla directory.

---

