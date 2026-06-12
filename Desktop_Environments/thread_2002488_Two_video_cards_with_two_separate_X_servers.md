---
title: "Two video cards with two separate X servers"
date: 2012-06-12
forum: Desktop Environments
---

### Post by Skaperen on 2012-06-12
Has anyone actually tried doing this, where they have two video cards ... but instead of having one larger logical display in a single session, they have two completely different sessions, each on a separate instance of X running?

It seems the most plausible way to set this up would be separate config files, each with specific coded busid parameters to direct each X instance to a specific video card.  Right now I am doing research to find out if this is even possible to do.  I don't have the means to test it, yet (planning phase).  And I don't know if there are other things I'd need to do for it.

What's it for?  I'm not in a position to say.  It's NOT end user desktops/seats.  No hardware keyboard or mouse is needed as long as the program that allows VNC to "tap in" to a running X session can work.  Only minimal access by that means is needed, if at all.  Think of a multiple display signage system where you have 60 displays.  If only once video card per machine can work, you need 60 machines.  If you can do two you only need 30 machines.  If you can do three you only need 20 machines.  This can go until you run out of usable slots or the machine capacity is exhausted (for heavy video updating, that exhaustion might be at 2 video cards, for example).

At this time I am only looking for any writeups where someone has actually done this, even if they don't provide all the technical details about how.  I'm more looking for what "gotchas" might be in the way.  So far, Google only finds cases where people are setting up multiple displays where they had to extend into multiple video cards (and a single instance of X running both).

I definitely need this to be separate instance of X for each video card.  I'd think that should be simple, and maybe it is.  But there might be issues with the two instances trying to access the same keyboard/mouse and refusing to run if it can't get access to hardware keyboard/mouse.

I'm planning to use Xubuntu on this, though I'd think it is likely the same for other editions.

---

