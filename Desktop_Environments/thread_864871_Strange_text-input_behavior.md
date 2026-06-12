---
title: "Strange text-input behavior"
date: 2008-07-20
forum: Desktop Environments
---

### Post by nesius on 2008-07-20
Just recently while typing in any text input widget in pretty much any application, my single-quote, double-quote, and carot (^) keys all require double-strikes to generate a character.  It seems I´ve somehow activated text-input mode where these are now escapes to enable special characters like é, ó, etc... I´ve no clue how I turned this on, and several hours of web searches and browsing preferences-dialogs have all lead to dead-ends?  Might someone know how I can revert my text-input behavior to what it used to be? 

Thanks in advance.

---

### Post by nesius on 2008-07-20
Fixed after the following long process.  

* Observed the wonky keyboard behavior occurred under a different user running an different desktop environment (fvwm).  

* Noted in my Ubuntu desktop env, typing "setxkbmap us" instantly restored expected behavior to that shell/window.  

* Re-examined keyboard preference, and noticed "US (intl)" was the default layout, and the ONLY layout.  

* Added a new layout - US - with no modifiers. 

* Set US to be the default 

At this point, the system-wide behavior was still incorrect.  Out of semi-desparation, I then did: 

* Delete the us (intl) layout from the list of available layouts, even though it is no longer tagged as the default layout.  

*POOF*  

All was well.  

Of course, the next question is "How did my keyboard layout get changed without me realizing it?"   I will probably never know, and at this point am not going to devote more time to it.

---

