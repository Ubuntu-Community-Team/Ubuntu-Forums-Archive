---
title: "[SOLVED] Non-default GUI terminal sessions break if de-selected"
date: 2008-01-26
forum: Desktop Environments
---

### Post by Phrawm48 on 2008-01-26
For Feisty (7.04) and Gnome.  Desktop computer with 1GB RAM and 160 GB disk.  I'm a reasonably competent Ubuntu user but not very knowledgable about Linux's / Gnome's / X's internal "plumbing".
[B]
[SIZE=4]WHAT I CAN DO -[/SIZE][/B]
I can readily use *CTRL+ALT+Fn* to move to a non-default (i.e. non-F7) terminal session, log in to that session, then use *startx -- :n* (where n > 0) to start Gnome in that session.  So far, so good.

**[SIZE=4]WHAT I CAN'T DO -[/SIZE]**
If I use *CTRL+ALT+F7* to redisplay my default GUI session, then *CTRL+ALT-Fn* back to the newly created GUI session, the new session's Gnome GUI is gone, replaced with a text-based screen containing the X startup sequence for that formerly GUI desktop session.

The only thing I've figured out how to do at that point is to use *CTRL+c* to stop the "broken" X session, then use *startx* to restart the GUI.  In other words, I remain logged in to that session but can't seem to create a second, persistent GUI session that I can use *CTRL-ALT-Fn* to leave and return to.

I'm probably making a relatively simple procedural mistake, but heretofore haven't played with multiple sessions very much.

Can anyone please suggest how I can configure or otherwise remedy this situation so that I can have multiple, persistent GUI terminal sessions?

Cheers & thanks,
Ric

---

### Post by Phrawm48 on 2008-01-27
Okay, I'm not sure I've solved my problem rather than found a circumvention to it.

I read somewhere that F9 through F12 were used for GUI virtual terminals ("vts").  It also seems to be a known Ubuntu (Linux?) behavior that the F8 virtual terminal (vt) displays the text-based trace of X activity for the default F7 GUI vt.

So I've conclued (at least for now) that the idea is to log into F1, use *startx -- :1* to start a new GUI vt, then "find" that session on -- and also to leave and return to it -- on CTRL+ALT+F9.  And so on up to F12...

So I'll consider the problem resolved, or at least circumvented, for the time being, even though I don't completely follow the rationale of creating something in one vt so I can run it another...

Cheers & hope this helps,
Ric
SFO

---

