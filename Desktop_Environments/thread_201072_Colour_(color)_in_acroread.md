---
title: "Colour (color) in acroread"
date: 2006-06-21
forum: Desktop Environments
---

### Post by jrb114 on 2006-06-21
Hi,

I'm trying to print a poster A0 size. I generated the file using scribus (1.3.3.2) and exported it to a pdf. The poster has transparencies etc, and my understanding is that these are all flattened when it becomes a pdf. 

To print the poster, I need to go to the graphics centre and they run windows (and whinge if you go along with a pdf "Where's your Powerpoint?" you get the idea). But generally, they are very good. I've now tried to print the poster twice, once it worked, but the colors looked washed out, and secondly they completely mucked it up.

The problem with the colors is that on my ubuntu box, with both acroread 7.05 and, having just installed it, acroread 7.08, the colors look lush and full. On Windows, using the latest acroread 7.07 & 7.08 they don't. This occurs on everyone elses machine in the office (they all use windows, and they all look washed out). This happens even when I've reproduced the pdf using scribus running on windows too.

To summarise:

Pdf produced on ubuntu: Colors fine on ubuntu; colors washed out on windows
Pdf produced on windows: Colors fine on ubuntu; colors washed out on windows

Short of persuading the graphics centre people to ditch windows, I don't know what to do. The final straw that made me think something weird was happening was when I used terminal server client to display the poster on windows acroread and using acroread read on ubuntu simultaneously. See screen cap attached.

Many thanks,

James

== edit 21 Jun 2006 ==

The next stage in the bizaare saga.

Printing on ubuntu through acroread (using lpr, postscript level 3, not lp) to make the postscript file looks fine. Display this on the windows box through ghotoscript and, violà, it's fine on windows too.

Something extremely weird seems to be going on with acroread. Now to persuade the graphics centre that they can cope with postscript (which is what they do anyway, but in a very prescribed manner).

Hmmm.

---

