---
title: "Konqueror folders not auto-refreshing"
date: 2005-04-29
forum: Desktop Environments
---

### Post by GeneralZod on 2005-04-29
Hi all,

Just a quick question about Konqueror 3.4.  In earlier versions, as long as famd was running, changes made to files that are currently displayed in Konquerors view pane were automatically shown in Konqueror (so e.g. if I opened /home/simon/tmp [which contains a file called "dummy", say] in Konqueror and then in Konsole I did echo Hello >> /home/simon/tmp/dummy, then the size of dummy would be shown to increase in Konqueror, as well as the modification date).

I tried this recently in Gentoo, and it didn't work; deleting and creating files was fine (they appeared and disappeared in the Konqueror window, as required) but just *changing* the files by e.g. appending to them did not - I'd have to manually refresh to see the changes.  So I installed Kubuntu on my laptop (I've been itching to try it out due to all of the great things people say about it! :)) and was disappointed to find that it did not work here either, with famd nor gamin.  So I wondered if it works at all for anyone else? I eventually got it to work my actually hacking part of the source code (with both famd and gamin; and with the latter, I could unmount CD-ROMs and USB pens, even if they were opened in Konqueror!!!   \\:D/  ), but I'd like to know whether this is a bug, whether it's just happening to me, or whether there is just some setting I needed to enable.

Many thanks in advance,
Simon

---

