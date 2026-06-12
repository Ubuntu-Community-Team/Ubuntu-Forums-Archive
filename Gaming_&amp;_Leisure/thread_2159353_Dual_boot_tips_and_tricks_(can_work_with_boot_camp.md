---
title: "Dual boot tips and tricks (can work with boot camp) and tweaks"
date: 2013-07-02
forum: Gaming &amp; Leisure
---

### Post by vanquishedangel on 2013-07-02
This may not be the right section but because I am now dual booting to game I thought this may be correct.

This may help in virtualization as well, I havent tested it. I have only tested windows 7 so far but it wont take that much googling to find information on others.

First I run a 64 bit ubuntu and have 8 gigs ram with amd dual core and ati 6450.

I installed tiny7, I have a windows key so all good there(this should work on regular windows also)

I installed a hard to find patch to enable windows7 32 bit to see and use all my ram, patch can be found here (may cause stability issues, but I have none):

[http://www.2shared.com/fadmin/51750417/2ead9912/win7-7600-4gb-patch.exe.html](http://www.2shared.com/fadmin/51750417/2ead9912/win7-7600-4gb-patch.exe.html) (the company that made the patch pulled it off thier website because two antiviruses labeled it a virus) the original post i found is here:

[http://www.bcastell.com/tech-articles/enabling-more-than-4-gb-of-ram-under-windows-7-32-bit/](http://www.bcastell.com/tech-articles/enabling-more-than-4-gb-of-ram-under-windows-7-32-bit/)


Windows sets a limit on ram that is a false limit (2gb if you are lucky), the operating system can use more but M$ needs money so home users have this false limit while M$ servers 2000+ can use more ram.

then I also added these strings to boot ini, by opening run from the start menu and running these commands:

BCDEdit /set PAE ForceEnable (enables pae in windows 7)

BCDEdit /set IncreaseUserVa 3072 (allows programs to use up to 3 gb ram instead of the usual limit per program)

my windows is now super speedy!

---

