---
title: "firefox won't start after installing netbook remix"
date: 2008-12-10
forum: General Help
---

### Post by plasmafusion on 2008-12-10
hey all
just installed netbook remix on top of 8.10 on my acer aspire one.
everything works well and i'm quite enjoying the interface but one error has occurred.
firefox (3.0.4) will no longer start. after clicking the icon it does its usual little flip...there's a busy mouse icon for a couple of seconds and then nothing. starting it from the usual ubuntu menu does the same thing.
the latest version of opera starts normally.
anyone got any ideas?
cheers.

---

### Post by easybake on 2008-12-10
what is the output from terminal when you type
firefox

---

### Post by plasmafusion on 2008-12-10
you know...i really should have thought of that...i was checking log files etc...
will post when i'm back in front of the machine tonight.
thanks for your reply

---

### Post by plasmafusion on 2008-12-10
output is as follows...

Error sanitizing history: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 115"  data: no]

firefox starts but everything has reverted to defaults (no add-ons, bookmarks, default homepage etc).
but at least it's starting :)
tried deleting all private data but error remains.
will try reinstalling foxmarks and a couple of other plugins and see how it goes.
thanks for your suggestion...don't know why i didn't think of it.

**EDIT** 
nope not a happy firefox. no settings stick. when i try and edit the privacy preferences the browser crashes. click the "google search" button on the main page...nothing happens.
will need to investigate further.
got opera synced with my mobile using opera mini 2 anyway so my bookmarks remain even if i can't get foxmarks running (could access the web version of foxmarks anyway)...one of my main concerns.
cheers

---

### Post by easybake on 2008-12-10
Apparently that problem can be resolved by [creating a new profile]("http://support.mozilla.com/en-US/kb/Managing+profiles"). 

Also the error can be from using a custom location probably something with the path displayed in the error.

---

### Post by plasmafusion on 2008-12-10
starting the profile manager and clicking create profile gives me

user@foobar:~$ firefox -ProfileManager
Segmentation fault

and crashes...harumph.

---

