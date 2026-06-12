---
title: "launching to the internet from a desktop window"
date: 2009-05-15
forum: Desktop Environments
---

### Post by walterramjet on 2009-05-15
I was trying to install Zimbra Desktop and got to the part where I setup my email account.  Its just a window on the desktop that you enter email address and password etc...  After everything is filled out, I click the button at the bottom that says "Validate and Save" and returned this error:

"www.hotmail.com:80" host not found. Please check hostname and network connectivity.
 
 I dont think it has anything to do with hotmal because there were several other internet links near the bottom of Zimbra email account setup dialogue box that also did not work. The links were valid. That is, if copied and pasted to the web browser, they worked, but from inside the dialogue box, clicking on them resulted in an error message that indicated a loss of internet connection. It almost looks like something is preventing internet communication from the account setup dialogue box.
 
 what could be the problem?
 
 Thanks,
 Walt
 
 p.s. this is what shows up in my "Error Console" during account setup, when I click the "Validate and Save" Button.
 
 Error: Cc['@mozilla.org/desktop-environment;1'] is undefined
 Source File: chrome://webrunner/content/webrunner.js
 Line: 177
 
 Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIWebNavigation.canGoBack]" nsresult: "0x80004005 (NS_ERROR_FAILURE)" location: "JS frame :: chrome://global/content/bindings/browser.xml :: get_canGoBack :: line 0" data: no]
 Source File: chrome://global/content/bindings/browser.xml
 Line: 0
 
 Warning: anonymous function does not always return a value
 Source File: [http://localhost:7633/zimbra/desktop/js/desktop.js](http://localhost:7633/zimbra/desktop/js/desktop.js)
 Line: 120, Column: 9
 Source Code:
 return true; 
 
 Error: Cc['@mozilla.org/desktop-environment;1'] is undefined
 Source File: file:///home/walter/zimbra/zdesktop/linux/prism/extensions/prism-runtime@developer.mozilla.org/components/nsPlatformGlue.js
 Line: 329
 Error: Cc['@mozilla.org/desktop-environment;1'] is undefined
 Source File: file:///home/walter/zimbra/zdesktop/linux/prism/extensions/prism-runtime@developer.mozilla.org/components/nsPlatformGlue.js
 Line: 329

---

