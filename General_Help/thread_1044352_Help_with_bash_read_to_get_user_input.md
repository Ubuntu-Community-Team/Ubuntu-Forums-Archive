---
title: "Help with bash read to get user input"
date: 2009-01-19
forum: General Help
---

### Post by sarang on 2009-01-19
Hello folks,
I had posted this in the programming sub-forum a while ago, but not many people seem to have seen it, so I am posting it here again.

           I have the following problem while trying to read the user's response from a bash script:

If the user continues to type things after my first [FONT="Courier New"]read[/FONT] has read whatever it wants (i.e one character if [FONT="Courier New"]-n1[/FONT] option is used, or till the newline character or IFS otherwise), those things are not discarded either by bash or my gnome-terminal (i.e the read buffer is not flushed). The result of this is that those characters are passed on as user input to my next [FONT="Courier New"]read[/FONT], causing problems. I have tried to overcome this by reading to an array (with [FONT="Courier New"]-a[/FONT]) and [FONT="Courier New"]unset[/FONT]ting the array before the next read, but that does not work.

How do I make this work?

Thanks in advance!

---

