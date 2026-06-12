---
title: "Webcollage screensaver fix after upgrade"
date: 2005-10-15
forum: Desktop Environments
---

### Post by agger on 2005-10-15
Today, I did a clean reinstall of Ubuntu (with my /home burned to a DVD and reinstated immediately afterwards), and I found that my chosen screensaver (the wonderful "webcollage") *didn't work*!

But all problems have their solution: Up to now, there has been a dictionary
(a word list) in /usr/dict/words. Webcollage (a Perl script) assumes there is
such a file, and fails (silently, without writing anything in the log files) when 
/usr/dict/words is not found.

First, quick-and-dirty solution to problem:

[FONT="Courier New"]sudo touch /usr/dict/words[/FONT]

This file doesn't have to have any contents, as the script also uses
/usr/share/dict/words, which is not empty in my default breezy install.

More lasting solution:
The official webcollage script should no longer reference /usr/dict/words,
or alternatively /usr/dict/words should exist.

Should I file a bug on this one, some somebody can have a look at it?

---

### Post by mlomker on 2005-10-15
> Should I file a bug on this one, some somebody can have a look at it?

It looks like the /usr/share/dict/words is in the **dictionaries-common** package.  The screensaver is in **xscreensaver-data**.  It sounds like one of those packages should be fixed...yeah, a bug report would be a good idea.

---

### Post by agger on 2005-10-16
OK, I submitted a bug - but of course, it can hardly be considered a high priority bug ... so if anybody wants to use this screensaver, there's a quick fix above.

---

