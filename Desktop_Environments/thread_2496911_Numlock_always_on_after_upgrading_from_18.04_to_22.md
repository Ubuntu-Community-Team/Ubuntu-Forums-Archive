---
title: "Numlock always on after upgrading from 18.04 to 22.04"
date: 2024-04-16
forum: Desktop Environments
---

### Post by SteveConleyGA on 2024-04-16
Yeah, it had been too long since I had upgraded my MythTV installation - because "if it works, don't break it" and it had worked perfectly for 4 years ...

But I finally decided it was time and I ran into a number of issues. 

This is the simplest one - and I will post about the others when I am confident.

I normally have Google find my support issues - because frankly, it is better at searching the various sites than ANYBODY's search engine - including the the really big corps.
So I was guided to this answer by a post I finally found and frankly forgot where.

The issue is that new code put in to solve problems apparently with some laptops, broke my desktop with a WIRELESS keyboard I use for MythTV.

ANSWER: traced the solution down to changing the file /etc/default/numlockx:
Last line of file was NUMLOCK=auto
That activated this new code.
So I changed to NUMLOCK=off

NOTE: The BIOS was set to NUMLOCK off and as I said it had worked since 2010 and all the prior versions.

The change that caused this was to the file /etc/X11/Xsession.d/55numlockx
In it you will see code concerning /usr/bin/laptop-detect.

When run on my machine - apparently because of the wireless keyboard, it THINKS I have a laptop and returns "1" or true.
I do not know why it does that - because it is definitely not a laptop and I don't know what the code does.

Anyway, I hope this helps someone ...
Steve

---

