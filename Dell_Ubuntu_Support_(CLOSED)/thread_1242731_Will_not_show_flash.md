---
title: "Will not show flash"
date: 2009-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dsextonj on 2009-08-17
My Dell froze up and I was left with having to turn the computer off. It was the last resort. When I booted it back up, Adobe Flash stopped working.

I'm using Ubuntu 8.04 with Firefox 3.5 and Adobe Flash 10.??? latest update.

If I go to youtube, I can see the video fine. I go to a site that has the video embedded, and the screen is blank. If I doubleclick the blank, Firefox goes dark and freezes up for a minute. Then it unfreezes, but the video still does not work.  I have flashblock disabled and javescript is enabled.

Any help will be appreciated.

---

### Post by mikewhatever on 2009-08-17
I'd assume, if you can play youtube videos, then flash is fine. Perhaps the other site's videos aren't flash at all?

---

### Post by Diskotekno on 2009-08-17
You could try removing and reinstalling the flash plugin and see if that helps.

Try: sudo apt-get purge adobe-flashplugin

and then sudo apt-get install adobe-flashplugin

---

