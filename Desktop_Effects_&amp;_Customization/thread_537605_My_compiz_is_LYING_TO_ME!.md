---
title: "My compiz is LYING TO ME!"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by bohsocks on 2007-08-29
Hi there....

I recently freshly installed Ubuntu (7.10) and tried to get compiz working.  After tinkering with drivers (ATI) and fglrx and XGL and all those good headaches.... I tried running compiz and it said:

rob@rob-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

But in my previous install I was running compiz... YESTERDAY on the same hardware!

What's the deal here.... I want my pretty windows back :(

---

### Post by Chymera on 2007-08-29
I'm pretty sure you should have posted this under "Development (Gutsy Gibbon)"... since it isn't a stable release yet, and thus not supported by all sections of the forum.

---

### Post by jhernandez1270 on 2007-08-29
try this I read it earlier in this forum from a guy who had the same error

in terminal search your xorg.conf file for Compsite with:

cat /etc/X11/xorg.conf |grep Composite

if it says Disable 
try Enable - ing it.

---

