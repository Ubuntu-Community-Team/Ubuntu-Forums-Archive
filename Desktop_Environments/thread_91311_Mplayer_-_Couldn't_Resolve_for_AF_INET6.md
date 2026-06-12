---
title: "Mplayer - Couldn't Resolve for AF_INET6?"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Darrin on 2005-11-16
When I click on web audio files and mplayer launches, I get the following error.

Couldn't Resolve for AF_INET6: (name of website goes here)

It seems to play the file fine. Just the error always pops up.

How do I correct this?

---

### Post by rboliver on 2008-02-14
I saw this reply on Mplayer HQ lists, and it worked for me:

"That's ipv6 pollution that's been occuring in nearly every 
program in existance for a while.  I say pollution because almost nobody 
uses ipv6 yet, and the default should still be ipv4.

Stick this into your config:

prefer-ipv4 = yes

And rejoice because your mplayer will no longer waste its time trying to 
use ipv6 first and fail."

Your config file should be in the folder .mplayer under your home directory.

I hope it helps.

Rubens

---

