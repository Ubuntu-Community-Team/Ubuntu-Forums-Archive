---
title: "Phatch won't work (yet) in Lubuntu 13.04"
date: 2013-04-27
forum: Desktop Environments
---

### Post by M_Mynaardt on 2013-04-27
Hi!

I just upgraded from Lubuntu 12.10 to 13.10 on my laptop yesterday.  It seems to be okay; for the most part.

However the application phatch won't work.  The first time I tried running it I got an error message and it didn't work.  Since there, I've reinstalled it, but when I try running phatch now, nothing happens.  No error message, no nothing.  Anyone know what could be causing this?

Thanks!

---

### Post by John Fraser on 2013-05-02
I am getting the same thing with Ubuntu 12.10 X64.
It's driving me mad. I've tried reinstalling phatch, but with no improvement.
When I try to open it I get a "Sorry, Ubuntu 12.10 has experienced an internal error" message. When I seek further details I get: "phatch crashed with NameError in NotifyingList():name '_module_' is not defined"

Here's hoping that someone can assist!

---

### Post by M_Mynaardt on 2013-05-03
> **John Fraser said:**
> I am getting the same thing with Ubuntu 12.10 X64.
It's driving me mad. I've tried reinstalling phatch, but with no improvement.
When I try to open it I get a "Sorry, Ubuntu 12.10 has experienced an internal error" message. When I seek further details I get: "phatch crashed with NameError in NotifyingList():name '_module_' is not defined"

Here's hoping that someone can assist!

At least I'm not the only one.  Hopefully they'll figure this one out soon.

I also updated my PC to Xubuntu 13.04 (my laptop runs on Lubuntu and I use Xubuntu on my desktop PC); and Phatch won't work on that either.  So there's something in *buntu 13.04 that disagrees with Phatch.  Whatever it is...
:(

---

### Post by muhh on 2013-05-25
Hi,

There is a solution here: [https://bugs.launchpad.net/ubuntu/+source/python-imaging/+bug/1112496](https://bugs.launchpad.net/ubuntu/+source/python-imaging/+bug/1112496)

Remove phatch from your computer, delete /usr/share/phatch folder, perform autoremove, autoclean, reinstall phatch and then go to /usr/share/phatch/phatch/lib/thumbnail.py and change[COLOR=#333333][FONT=Ubuntu Mono] [/FONT][/COLOR]"import PngImagePlugin" in line 62, to "from PIL import PngImagePlugin".

And it works!

---

