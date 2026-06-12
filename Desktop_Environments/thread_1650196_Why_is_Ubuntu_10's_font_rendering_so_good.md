---
title: "Why is Ubuntu 10's font rendering so good?"
date: 2010-12-21
forum: Desktop Environments
---

### Post by Danny Darko on 2010-12-21
Hi all,

I've been Googling around trying to find out what makes fonts look so much nicer in Ubuntu than any other Linux distro. I've tried to make Fedora 14 looks as pretty, following recommendations to install freetype-freeworld (whatever difference that makes) and enable auto hinting in /etc/fonts/conf.d and such.

Nothing seems to work, so I wondered if anyone here knew what sort of trickery has been used in Ubuntu. I'm not looking to move away from Ubuntu any time soon by the way!

:-k

---

### Post by 3Miro on 2010-12-21
Under XFCE I got Anti-aliasing + slight hinting + RGB sub-pixel order (under Appearance). This works great with DejaVu, Liberation and Ubuntu fonts.

I am not sure about Gnome. You can try to mimic the settings, but there may be something different to tweak as well.

---

### Post by Danny Darko on 2010-12-22
> **3Miro said:**
> Under XFCE I got Anti-aliasing + slight hinting + RGB sub-pixel order (under Appearance). This works great with DejaVu, Liberation and Ubuntu fonts.

I am not sure about Gnome. You can try to mimic the settings, but there may be something different to tweak as well.

Thanks, doesn't look like it's the fonts themselves though. It seems to be to do with the anti-aliasing and / or hinting. The difference between Fedora 14 and Ubuntu 10 is really noticeable. Ubuntu's fonts look smoother and less fragmented (see attachments).

I would be really interested to know how these settings were achieved in Ubuntu; it's starting to rival OS X in its prettiness!

---

### Post by tpprynn on 2010-12-22
I've asked and googled about this before. The drastic improvement came in 9.04. There doesn't seem to be anything special in fonts.conf but I did read something about a libcairo patch that people who use Debian were adapting from Ubuntu. I don't understand it enough to pursue it.

My fonts are always 8 point (Deja Vu Sans) or 9 point (Segoe UI copied from my Vista disc) too - they're much sharper at that size even if it takes a small bit of time to get used to it. I'm very short-sighted but it's not a strain.

It's odd that the other distros don't use whatever file does the job when there's no money involved.

---

### Post by Danny Darko on 2010-12-22
> **tpprynn said:**
> The drastic improvement came in 9.04. There doesn't seem to be anything special in fonts.conf but I did read something about a libcairo patch that people who use Debian were adapting from Ubuntu. I don't understand it enough to pursue it.

That's pretty much where I got to. I found this:

[http://lovingthepenguin.blogspot.com/2010/07/ubuntu-font-rendering-in-debian-squeeze.html](http://lovingthepenguin.blogspot.com/2010/07/ubuntu-font-rendering-in-debian-squeeze.html)

*To get Ubuntu font rendering in Debian Squeeze, we need to download,  patch, rebuild, and reinstall the libcairo2 package. If this breaks  your system don't sue me. I am not an expert nor do I play one on  TV.*

Seems to be down to "David Turner's ClearType-like LCD filtering  patch and fix". Could be an interesting exercise trying to get this to work on Fedora.

---

### Post by Danny Darko on 2011-06-21
Turns out this is all to do with the lcdfilter patch after all. This raises a few other questions but it's progress. Thanks to everyone who replied.

---

