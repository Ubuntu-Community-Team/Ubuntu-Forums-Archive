---
title: "Thunderbird - Multiple Instances? - Without the Profile Manager"
date: 2005-01-13
forum: General Help
---

### Post by ayam on 2005-01-13
The subject is not very descriptive as I am not sure how to describe my problem succintly.

Anyway. The Thunderbird Profile Manager opens up When I click on a mailto: link in Firefox when I already have Thunderbird already running. My expectation is that a Thunderbird Compose windows opens. 

This also happens when I click on the Thunderbird icon when there is an already existing Thunderbird window running. On the other hand, Firefox just opens up a new browser window; on other distros and perhaps even in Windows the Firefox/Mozilla/Netscape profile manager opens up. 

How can I make Thunderbird not open up its profile manager? I've downloaded Thunderbird 1.0 from the backport and made it my default mailer by following these
[Wiki Instructions](http://http://www.ubuntulinux.org/wiki/ThunderbirdDefaultMailerHowto/view?searchterm=thunderbird) 

Thanks

---

### Post by steffen on 2005-01-18
This is what I added as the link to Thunderbird in my Opera. Works great with Opera, although I haven't figured out how to add the actual email address. But it does open a compose window, instead of the Profile Manager, as was previously my problem:

*mozilla-thunderbird -compose %s*

---

