---
title: "Firefox Exceptions on Run"
date: 2009-01-27
forum: General Help
---

### Post by nvikram on 2009-01-27
Hello,

When I start firefox, the browser loads, but the screen is blank and i cant use the forward,back,refresh,stop buttons. In the error console I get back 2 errors on startup.

1. 
Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.5/components/nsBrowserGlue.js :: bg__initPlaces :: line 449"  data: no]
Source File: file:///usr/lib/firefox-3.0.5/components/nsBrowserGlue.js
Line: 449

2.
Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]

If anyone could help me with this,
Thanks.

---

