---
title: "Window Focus"
date: 2009-01-19
forum: Desktop Environments
---

### Post by triplemaya on 2009-01-19
Sometimes when I create a new window it comes up ok, but does not have the focus. ( this is really tiresome when it is not the window I want, so I alt f4 it away, but I've gotten rid of the directory I found the file in, so I not only have to now get rid of the window I don't want, I have to go hunting for that directory again! )

I found the thread "new window don't have focus", but I tried both of the fixes suggested by yleeyas and made no difference. My preference called: browser.tabs.loadDivertedInBackground is already set to false, and I have no applications running with 'always on top' enabled, or not set like that by me anyway, and none that do that behavior that I have noticed.
I also found the thread "Hoary : window focus ? " which describes this sort of problem, but in that thread Santiago states "It is a known bug and gnome people is working on it.", but I am running Intrepid. If the bug has been fixed I seem to have some other kind of problem.

I don't know if it is a part of the same problem or something different, but I also sometimes find that when I open windows on one desktop and then move to another, all of the windows on the other desktop show up when I alt tab from one window to another. ( This is very tiresome because if I have open 20 or so firefox windows on some other desktop and I am looking for the one firefox window I have on the desktop I am working on, amongst a blizzard of other kinds of windows, there's only a very small chance of getting the right one. )
Naturally enough if I get the wrong one nothing happens.

Any help much appreciated.

---

### Post by mcduck on 2009-01-19
So you have desktop effects enabled? In that case install compizconfig-settings-manager and under general settings there's option for "focus stealing prevention" (might be called with a slightly different name in current version). Change that to "low" or disable completely.

---

### Post by triplemaya on 2009-01-19
Thanks mcduck I'll give that a try

---

### Post by triplemaya on 2009-01-20
Didn't work.
It's called 'Focus Prevention Level', and it was already set to low, set it to Off, but no improvement.

BTW mcduck, presuming that your signature is 'the answer' have you any new info on 'the question'?!

---

### Post by mcduck on 2009-01-20
> **triplemaya said:**
> Didn't work.
It's called 'Focus Prevention Level', and it was already set to low, set it to Off, but no improvement.

BTW mcduck, presuming that your signature is 'the answer' have you any new info on 'the question'?!

Nope, nothing we could understand. Since the question was "what you get if you multiple six by nine?" and the result doesn't really work I can only tell that there's something wrong with our universe. :D

Sorry, can't help you much with either question. The only problems with window focus I've ever had were cause by the focus stealing prevention feature of Compiz..

---

