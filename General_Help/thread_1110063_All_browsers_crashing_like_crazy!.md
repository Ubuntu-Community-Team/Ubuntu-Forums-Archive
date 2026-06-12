---
title: "All browsers crashing like crazy!"
date: 2009-03-29
forum: General Help
---

### Post by Nevon on 2009-03-29
Recently all browsers have been crashing more or less constantly. At first I thought it was just a Firefox problem, as that is my main browser, but then I noticed that Epiphany, Opera and Midori all had the same problems. I tried running Firefox from the terminal to see if it would spit out some kind of error message, and it did:
```
stub: GetFlashPluginVersion
Greasemonkey getFirebugConsole() error:
(new TypeError("chromeWin.Firebug is undefined", "file:///home/nevon/.mozilla/firefox/6c72dk1w.default/extensions/%7Be4a8a97b-f2ed-450b-b12d-ee082ba24781%7D/components/greasemonkey.js", 392))
Aborted

```
It says something about Greasemonkey, however, Greasemonkey isn't installed in the other browsers - so that can't be it. 

I've been trying to get an error message from the other browsers aswell, but of course now they won't crash.

---

### Post by ethoxyethaan on 2009-03-29
run firefox like this:
(caps matter)

firefox -ProfileManager

make a new account and try to use it.

---
try deleting the plugin directory:

rm -dr ~/.mozilla/plugins/

---

---

### Post by Nevon on 2009-03-30
> **ethoxyethaan said:**
> run firefox like this:
(caps matter)

firefox -ProfileManager

make a new account and try to use it.

---
try deleting the plugin directory:

rm -dr ~/.mozilla/plugins/

---

I tried that, and it didn't work. ~/.mozilla/plugins/ didn't even exist. Now how do I change back to my old profile? This new one obviously doesn't have all my bookmarks and stuff.

---

### Post by j7%&lt;RmUg on 2009-03-30
Uninstall greasemonkey if its still installed.

If you have Firebug installed uninstall it. Then try starting firefox both with and without the terminal.

If none of the above works then try google searching for "firefox crash fixes" and see what you can find.

Hope this helps.

---

### Post by Nevon on 2009-03-30
> **nisshh said:**
> Uninstall greasemonkey if its still installed.

If you have Firebug installed uninstall it. Then try starting firefox both with and without the terminal.

If none of the above works then try google searching for "firefox crash fixes" and see what you can find.

Hope this helps.

Firebug was never installed, and greasemonkey isn't installed on this profile. Besides, neither of them were installed in any of the other browsers. The only browser that won't crash on me now is elinks. :P But seriously, I like having images and being able to use the mouse when browsing the intrawebs. 

Google hasn't given me a lot of help either. I've only been able to found unrelated and/or old bugs.

---

### Post by j7%&lt;RmUg on 2009-03-30
Well that is strange.

EDIT:Try reinstalling flash, if that doesnt work then also see the file path after where it says "ChromeWin.firebug is undefined" go to that path and delete that greasemonkey.js file.

---

### Post by Nevon on 2009-03-30
> **nisshh said:**
> Well that is strange.

EDIT:Try reinstalling flash, if that doesnt work then also see the file path after where it says "ChromeWin.firebug is undefined" go to that path and delete that greasemonkey.js file.

I tried reinstalling flash. Removing that greasemonkey file isn't necessary, as Greasemonkey isn't installed on this profile or in any other browser - and they still crash. Interestingly enough, Firefox doesn't give any kind of error message when crashing. It just says "aborted". Same goes for the other browsers. The error message given in the first post wasn't actually an error message, it just happened to be there before the browser crashed.

---

