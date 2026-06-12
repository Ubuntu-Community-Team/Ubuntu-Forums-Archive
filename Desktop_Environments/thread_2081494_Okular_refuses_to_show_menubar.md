---
title: "Okular refuses to show menubar"
date: 2012-11-07
forum: Desktop Environments
---

### Post by fugue137 on 2012-11-07
As of a month or two ago, Okular stopped showing the menubar.  Among things, that means that it can't print anything.

A quick search of the fora reveals that "Ctrl+M" should show a hidden menubar.  It doesn't.  Right-clicking on the document pops up a dialogue that offers "Show menubar".  Clicking on it also does nothing.  No errors appear either on screen or to stderr.

I'm running a mishmash that includes KDE with Sawfish as my windowmanager (using $KDEWM), but I hope that's not relevant (and if I'm exceptionally lucky I'll be able to fix this without logging out (I have a few non-headless (headed?) matlab jobs that have made days of progress at this point)).

I thought I upgraded to Ubuntu 12.10, but /etc/issue tells me that I'm on 12.04.1.  Running KDE (and Okular) 4:4.8.5-0ubuntu0.1

Any thoughts would be much appreciated.

---

### Post by Zorael on 2012-11-09
Have you tried renaming the okular settings file(s)? Perhaps there's something wrong there that it just isn't dealing with gracefully.

I'm not at my machine, but going by convention the settings file should be at **~/.kde/share/config/okularrc** or so.

Failing that, have you tried starting KWin (temporarily), with **kwin --replace**? That's assuming it actually starts and doesn't defer just everything to your other manager as per your settings.

edit: nevermind, you said it didn't output anything to stderr. Mind that you may not have its debugging output enabled though, in **kdebugdialog**.

---

