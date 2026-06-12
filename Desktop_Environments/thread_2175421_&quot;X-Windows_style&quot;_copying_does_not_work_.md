---
title: "&quot;X-Windows style&quot; copying does not work any more"
date: 2013-09-19
forum: Desktop Environments
---

### Post by Ulrich_Grn on 2013-09-19
Hi all,

since I reinstalled Kubuntu 12.04, on both my laptop and my desktop, the "X-Windows style" copying does not work any more. That means, copying to clipboard by selecting the text and pasting through pressing both mouse buttons simultaneously, does not work any more. I can only use CTRL-C end CTRL-V, or the 'right clicking' menu entries.

I tested this misbehaviour with another user (on the same installation), and the result was the same. This suggests that the fault is not to be found on user level (i.e. in the home directory).

Does anyone have a clue?
Where, in which config file, is this "X-Windows style" copying feature configured?

Thank you very much for your help.
For me, the "X-Windows style" copying feature is one of the fine advantages of Linux over any other OS.

---

### Post by TheFu on 2013-09-19
I agree.  I've noticed that more and more programs are not honoring the select/paste that we've loved for 30+ yrs - X-buffer is the formal name.  It is limited when compared to other "clipboard" apps, but so very, very, very convenient.  These apps are going out of their way to block the X-buffer from being used.  I first noticed it on Firefox and Thunderbird about 8 yrs ago.   If you are seeing it more under KDE, I suspect the KDE core devs have started using a library that does this by default.  Did you install 12.04.1 or 12.04.3?  The core libraries were upgraded between these - I'm positive that kernel versions are different between .1, .2, and .3 releases.  If you upgrade from .1 ---> .3, you'll have an older, maintained, kernel.

There really isn't any work-around with the OS if that is what is really happening. Dropping back to an older 12.04 release and patching to current levels is my only suggestion.  I use LXDE and haven't noticed the issue as much ... just sayin' ;)

---

