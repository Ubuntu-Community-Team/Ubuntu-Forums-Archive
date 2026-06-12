---
title: "32-bit to 64-bit Natty...but keep apps and settings?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by Mrich1976 on 2011-05-04
Ok...Here's my situation:

I have upgraded to Natty 11.04 32-bit. I'm considering going to Natty 11.04 64-bit.

I'm just wondering if I can do that, and keep all the apps I have already downloaded and installed. I have several development tools, some games and educational apps for my son.

So, basically, I'd like to go from 32 to 64 bit, and keep all my apps and settings.

Can I do that?

---

### Post by movieman on 2011-05-04
Most of the settings should be stored in your home directory and I doubt the file formats are different between 32-bit and 64-bit in most cases. So if you keep /home as is then installing the 64-bit version of the OS would probably work (note that I haven't tried it myself so I can't guarantee that).

I believe apt has an option to dump out a list of installed applications which you can then pass back to it to tell it to install all the applications on the list; so as long as they aren't 32-bit specific you could dump out the list before the upgrade and then install all of them afterwards.

You would lose settings that are in /etc, like WLAN configuration.

---

