---
title: "Where is /usr/include/X11/keysymdef.h?"
date: 2010-04-21
forum: Desktop Environments
---

### Post by cafewalter on 2010-04-21
I'm trying to edit my .Xmodmap to get shift_tab working - right now, it seems to be mapped to nothing at all.

So I want to find the list of keysyms.  I see a lot of web pages saying it is in /usr/include/X11/keysymdef.h.

But for me, the only thing in /usr/include/X11 is a 'bitmaps' subdirectory; there are no .h files.

Do I need to install some additional package?  If so, what?  (I'm an Ubuntu newbie, but an experienced developer.)

Thanks for any help!

---

### Post by cafewalter on 2010-04-21
Answering my own question: sudo apt-get install x11proto-core-dev

However, I'm still not sure what I should map Shift+Tab to in order to make apps recognize it as a backtab rather than forward tab.  Nor do I know how to get Alt+Tab to work.

I'll mark this thread as 'solved' and start a new thread with those questions once I can articulate them.

---

