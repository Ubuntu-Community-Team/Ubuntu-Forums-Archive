---
title: "StarOffice Beta 6 Installation Problem"
date: 2006-06-11
forum: Desktop Environments
---

### Post by tepidpond on 2006-06-11
I hope I have the right forum for this:

At work the systems are severely locked down and the netwok is thoroughly filtered. The only office suite available is StarOffice 6(running on ancient Solaris boxen). I have been tasked to work on a heavily macro-dependent StarCalc document in my "spare time" at work. Unfortunately there is no documentation of StarOffice 6 at work.
I've managed to acquire the **beta** of StarOffice 6, and have high hopes of installing it, in order to test things at home where I have access to actual documentation.
The files I was given are: 
fd6ff8f5c8b828a285c023db3fa8c232  so-6_0-beta-bin-linux-en.bin
6730012c10aaca414a16c24a8faff84b  soa-6_0-beta-bin-linux-en.bin
638ebdb9ca5ae234c14c8a34dc4899a6  sop-6_0-beta-bin-linux-en.bin

When I start any of the three files in a terminal, it prints:
"glibc version: 2.3.6"
The screen will briefly display a grey box with the text: "Script file is now being read, please wait". Once that disappears, the main installation window appears for a fraction of a second, then vanishes. I've run find(1) on both /var/tmp and /tmp hoping it had extracted before crashing with no luck.

At the moment, I suspect that my glibc version is the issue...2.3.6 is considerably more modern than the 2.0 or 2.1 that was around when the thing was released.

So, I have a two-part question: 1) Does anybody know how to have two versions of libc installed without causing severe issues; or 2) Does anybody know why this thing is refusing to install?

Thanks for your time.

---

