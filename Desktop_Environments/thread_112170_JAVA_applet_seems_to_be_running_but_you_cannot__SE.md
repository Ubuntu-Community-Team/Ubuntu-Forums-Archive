---
title: "JAVA applet seems to be running but you cannot _SEE_?"
date: 2006-01-03
forum: Desktop Environments
---

### Post by r0ll3r on 2006-01-03
Hi there,
i have found a strange java error if you encounter the following situation.

I was starting with Firefox 1.0.7 and Blackcomb java. Of course, when Firefox 1.5 came out, i followed the HOWTO. I also upgraded to Sun Java. For me, it was working perfectly, but the other user account (namely, my girlfriend) cound not _SEE_ any java applets. When a java applet finished loading (status bar was informing me what applet has been loaded), the applet blinked up for a 0.2 sec, then turned into gray or white box. Nothing more.

Finally i found out what happened. When i followed the Firefox 1.5 HOWTO, i moved my ~/.mozilla to ~/.mozilla-old. Unfortunately, this was not done for my girlfriend. I narrowed down, that the source of the problem was the AdBlock plugin 0.5.2.039 in ```
~/.mozilla/firefox/XXXXXX.default/extensions/{XXXADBLOCKXXX}/
```

So deleting this dir and its contents solved all my headaches. But what was blocking every java applet in AdBlock? I dunno. But if you encounter this problem, you know what to do know. _Follow_ the HOWTO. In all cases.

---

### Post by amohanty on 2006-01-03
In the bottom right of the status bar you will see the adblock thingy. click on it - anything in brown italics is being blocked. if you click on it you will see the offending entry in the adblock filters that is causing it to block. Remove or modify that filter entry in adblock.

HTH
AM

---

### Post by r0ll3r on 2006-01-04
[QUOTE=amohanty]if you click on it you will see the offending entry in the adblock filters that is causing it to block. Remove or modify that filter entry in adblock.[/QUOTE]

There were no blocked entries. This is _not_ my case.

---

### Post by amohanty on 2006-01-04
That is strange. But doesnt removing the adblock folder throw away all your adblock settings?

AM

---

### Post by r0ll3r on 2006-01-04
[QUOTE=amohanty]That is strange. But doesnt removing the adblock folder throw away all your adblock settings?[/QUOTE]

Yes, i belive if i throw it away, settings will be gone too. But i remember, when i switched from Firefox 1.0.7 to 1.5, the actual AdBlock was not working with this very new version of Firefox. AdBlock was complaining all the time, so I had to disable it. There was an AdBlock Plus, which was working though, but later the AdBlock plugin was updated to work with FF 1.5.

So I think this is a special situation, maybe it won't happen anymore to anyone, but if somebody will search on it, this might be the solution of his problem.

---

