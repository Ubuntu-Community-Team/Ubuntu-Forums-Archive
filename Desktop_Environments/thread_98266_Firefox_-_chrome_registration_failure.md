---
title: "Firefox - chrome registration failure"
date: 2005-12-02
forum: Desktop Environments
---

### Post by slrafal on 2005-12-02
Could someone please shed some light on the following error in firefox.

"Chrome registration failed"

This error appeared when I tried to install the weather extension in firefox. How can I fix this error, so I can get the weather extension to work?

---

### Post by jrib on 2005-12-02
what version of firefox?

I get these errors using firefox 1.5 when I install new extensions.  I have my suspicions that it is because firefox doesn't have root priveleges but haven't test it out.  Things usually work fine despite these errors however.

---

### Post by slrafal on 2005-12-02
This is with firefox 1.5

---

### Post by slrafal on 2005-12-02
Well, forget it. I restarted firefox and the weather extension now works. But what is that Chrome error anyways?

---

### Post by nozdormu on 2005-12-03
[QUOTE=slrafal]Well, forget it. I restarted firefox and the weather extension now works. But what is that Chrome error anyways?[/QUOTE]

I don't know the exact cause, but disabling the Talkback extension makes it go away.

---

### Post by cjazz on 2005-12-03
Frankly, I'd like to know, too. I encountered it several times when I first installed Firefox 1.5, before installing any added extensions (DOM Inspector 1.8 and Talkback 1.5 were installed by default). It gave me no real problems; Firefox ran without further incident. But still I'm wondering. Curiosity can be a curse.

---

### Post by nischg on 2006-01-11
Extracted from Ubuntu Wiki's FirefoxNewVersion found at [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

"You may get an error dialog (twice) each time Firefox starts up saying Firefox could not install this item because of a failure in Chrome Registration. Please contact the author about this problem.. This is due to [WWW] this bug. To work round do the following:-

sudo touch /opt/firefox/extensions/talkback@mozilla.org/chrome.manifest  "

---

