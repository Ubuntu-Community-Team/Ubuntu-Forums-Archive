---
title: "Remove &quot;Set up mail...&quot; in 11.10"
date: 2011-11-29
forum: Desktop Environments
---

### Post by zaiger on 2011-11-29
Yes hello,

I have been trying to remove the "Set up mail..." option from my notification drop-down menu without much luck. I use Gmail, so I have no use for Thunderbird really so I removed it. It seems (from threads I found in a Google search trying to solve this on my own) that in previous versions you could remove evolution-indicator and that would solve the issue. In 11.10 the default mail client is not Evolution, but Thunderbird obviously, and removing the Thunderbird-notifier did not remove the "Set up mail..." entry, even after a reboot.

Does anyone know of a way to resolve this in Oneiric? Thanks in advance.

---

### Post by zaiger on 2011-11-29
First, the thread title tag is wrong. It's Ubuntu not Lubuntu, that is probably my fault.

Ok so what I did to fix this was go to > /usr/share/indicators/messages/applications 
and removed all of the files that I didn't want in my notification bar (Backing them up to a file on my desktop of course, just in case Murphy's law came into effect).

---

