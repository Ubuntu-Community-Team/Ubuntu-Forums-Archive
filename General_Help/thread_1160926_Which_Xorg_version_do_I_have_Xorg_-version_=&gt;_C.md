---
title: "Which Xorg version do I have? Xorg -version =&gt; Confusion"
date: 2009-05-16
forum: General Help
---

### Post by bernd.juchems on 2009-05-16
Hi folks ...

I have some major problems with my damn ATI Mobility Radeon X1900 in my Fujitso Siemens Amilo Xi 1554, which is not supported by FSC, AMD/ATI or any other vendor I tried in countless hours of frustrating search at all.

Anyway, with accepting some trade-offs I'm able to work with my NB and Ubuntu (not mentioning watching movies or something like this).

But:
For some survey from AMD for my user experience (hell, their ears will ring), I am asked for my Xorg-Version I am currently using (lately switched to Jaunty).

So, searching for answers I find: "Xorg -version".
This gives me:
> X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ju-augustus 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.


All right ... 1.6.0 ...

And how does this fit with all the "Version 7.4", "Version 6.9" and so on, all the other Xorg users are talking about? That survey has a DropDownbox with Xorg versions from 6.7 to 7.4.

How does my 1.6.0 fit in?

Besides: in the examples for "Xorg -version" all the other people are getting "6.9" and so on.

What do I do wrong?

Please help ...

Bernd

---

### Post by quixote on 2009-05-17
Those 6, 7, 8 numbers sound like the versions for ATI proprietary drivers for xorg, rather than the xorg versions themselves.  Those are in the 1.something range, as you say.

I don't know how you'd go about finding the ATI version number, but maybe the ATI web site would have something on that.

---

