---
title: "My problems compilation"
date: 2006-10-16
forum: Desktop Environments
---

### Post by benjaminzsj on 2006-10-16
Recently, I come across several weird problems when tailoring my Dapper.
First, please take a look at the screenshot attached, these malfunctioning drive icons won't let me access them by double clicking. This occurred right after I installed some standalone deb packages, I'm not sure if they're connected.
Secondly, the time for Firefox to look up a site turns out much longer than before, but the transfer speed is normal e.g.: http download etc. And weird thing is that this doesn't happen to my XP on the same machine(dual boot), I don't know if any of those programming setup(LAMP, RubyonRails) may be the cause.
Third, I wonder whether it's wise for me to compile a latest kernel on my Dapper, I just need some announced speed improvement, but this is considered unstable, isn't it?
Last and the most frustrating, I can't setup my beryl/AiGLX on my Intel GMA900 graphics, everything required were installed successfully but whenever I start beryl from the tray icon, I'm kick out of session and taken back to login screen. I strictly followed the corresponding official beryl wiki, so stricted that I even add a new dbe module to the module list. I proposed my problem to the beryl forum but no luck, so I don't expect this one to be answered and solved.
Sorry for bursting so many troubles,:) looking forward to your kind response.


[COLOR="DarkRed"]No way! All my icons are gone, all known files types are now with default unknown icons. Is there something wrong with MIME type?[/COLOR]

---

### Post by kuja on 2006-10-16
With compiling a new kernel I don't think you'll see a pronounced improvement in speed, not really worth the effort to bother. How much longer does it take for a site to show up? I tend to have similar problems, usually occurring during DNS resolution. Try switching DNS servers (should be able to set it in /etc/resolv.conf).

---

### Post by benjaminzsj on 2006-10-16
> **kuja said:**
> With compiling a new kernel I don't think you'll see a pronounced improvement in speed, not really worth the effort to bother. How much longer does it take for a site to show up? I tend to have similar problems, usually occurring during DNS resolution. Try switching DNS servers (should be able to set it in /etc/resolv.conf).
Thanks for the tip.
The "Look up ..." message may stay 10+ seconds longer in the status bar while the window's blank whereas the contents come up swiftly.

Having checked my resolv.conf, the top line reads "search login", followed by some nameservers which I've seen in XP configuration. And according to what can I modify them?

---

