---
title: "javascript doesn't always work"
date: 2005-08-28
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-08-28
Hi

Is there a way to improve javascipt in rendering of pages or menus. An example of this is this page:

[www.svebo.se](www.svebo.se)

When i try and use the menu alternatives it doesn't work and the javascript console gives this error:
> 
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

Anyone that knows how to improve javascipt in linux?

---

### Post by incinerator on 2005-08-28
1.) Try another web browser, if the page does not work in firefox it might work in konqueror and vice versa.

2.) Check the web browser's javascript settings. The default configurations are quite restrictive compared to <obsolete_os_browser>, preventing certain kinds of pop-up windows from opening and other stuff. In firefox, the extended javascript options can be found in the Options -> Web-Features -> Javascript -> Extended dialog. In konqueror they can be found in the Settings -> configure konqueror menu, there is a dedicated java/javascript button you can click to get to the right panel.

On my box both konqueror (from KDE 3.4.2) and firefox (1.0.6) seem to render that page nicely and without errors.

---

### Post by weeroona on 2005-08-28
For java applets, I believe you need Java installed. (check the [ubuntuguide.org/#jre](ubuntuguide.org/#jre)) 
Using firefox 1.06 with javascript enabled, the page loaded for me.

---

### Post by Jeezis on 2005-08-28
worked fine for me using konqueror. i have the jdsdk installed and haven't had a problem with javascript or java. i recommend checking the above link.

---

