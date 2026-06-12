---
title: "Bug with Epiphany and keyword URL"
date: 2006-10-28
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2006-10-28
I updated from Ubuntu 6.06 to 6.10, updating GNOME and Epiphany to 2.16.1.

When I type a composed keyword (ie. "the keyword") in Epiphany address bar, instead of using the default search engine (defined by the *keyword.URL* key in about:config) it throws *"The URL is not valid and cannot be loaded"*. However if use a simple keyword (ie. "keyword") it works.

As [umarmung]("http://gnomesupport.org/forums/viewtopic.php?p=54114#54107") told me on GNOME Support Forums, this is a bug. And the question is, as Ubuntu Edgy is now released, containing this bugged version, and as updates are only made for security issues, does it mean that this bug will reside until Feisty in 2007/04?

Gabriel Bauman said on the [Bugzilla page]("http://bugzilla.gnome.org/show_bug.cgi?id=350053") that Ubuntu may be updated with the fix. Will it? When?

---

### Post by Wolki on 2006-10-28
> **Jonathan Métillon said:**
> 
Gabriel Bauman said on the [Bugzilla page]("http://bugzilla.gnome.org/show_bug.cgi?id=350053") that Ubuntu may be updated with the fix. Will it? When?

Well, if the fix is in Gnome 2.16.2 (which I assume it will be), the fix will be inlcuded then at the latest. There were quite some dupes on that bug, and someone has already written a patch for the current version, so we might see it a bit earlier.

Here's the Malone bug: [https://launchpad.net/distros/ubuntu/+source/epiphany-browser/+bug/56610](https://launchpad.net/distros/ubuntu/+source/epiphany-browser/+bug/56610)

---

### Post by Jonathan Métillon on 2006-10-28
Thank you Wolki. What is the edgy-updates ? Is that a software source (repository)?

---

### Post by Wolki on 2006-10-28
Yes. edgy-security contains security updates, and edgy-updates contains normal updates. If you don't have it enabled, use the repository settings tool.

---

### Post by Jonathan Métillon on 2007-01-18
In Administration > Software Sources, Internet Updates tabn, I only have Proposed updates that is unchecked.

Is this what you call edgy-updates? Should I check it?

---

### Post by Jonathan Métillon on 2007-01-18
I checked *Proposed updates* and I updated my system. A lot of packages were updated.

But I didn't see the Epiphany package updated. And the keyword URL bug is still present.

So, is this issue fixed for Edgy or not? Should I wait for Feisty for it to be fixed?

---

### Post by deadlydeathcone on 2007-01-18
It's fixed in Feisty, but not Edgy and I don't think that it ever will be. I have a custom version of Epiphany with tons of upstream patches and some from AqD that fix this bug and add various improvements (forcing all links to open in new tabs, implementing session-saving, replacing some legacy icons with Tango ones etc). You can get it [here]("http://lightofcracker.com/ubuntu/epiphany-aqd3.tar.gz") if you like.

---

### Post by Jonathan Métillon on 2007-01-19
I just installed your custom version of Epiphany and it ROCKS!

Thank you so much Deadlydeathcone!

---

### Post by Wolki on 2007-01-19
> **deadlydeathcone said:**
> It's fixed in Feisty, but not Edgy and I don't think that it ever will be. 

I heard that it will be fixed for edgy, someone made a patch. We'd have it for a long time if the update policy hadn't changed. :-/

> I have a custom version of Epiphany with tons of upstream patches and some from AqD that fix this bug and add various improvements (forcing all links to open in new tabs, implementing session-saving, replacing some legacy icons with Tango ones etc).

Sounds very interesting. Two questions:
- I absolutely hate forcing new windows into tabs. Is it configurable?
- Session saving already seems to work find on my standard epiphany. What does change there?

---

### Post by Jonathan Métillon on 2007-01-21
> **Wolki said:**
> - I absolutely hate forcing new windows into tabs. Is it configurable?
- Session saving already seems to work find on my standard epiphany. What does change there?
[LIST]
[*]If it's possible, I didn't see how. I looked in Edit > Preferences. By the way, you need some time to accomodate this. Sometime you are waiting for a window to popup... but then you realize it's already opened in a tab!
[*]I didn't see what changer in session saving. When Ephy close unexpectedly, it offers me to restore the session on next launch. As usual.[/LIST]

---

### Post by deadlydeathcone on 2007-01-21
> **Wolki said:**
> Sounds very interesting. Two questions:
- I absolutely hate forcing new windows into tabs. Is it configurable?
- Session saving already seems to work find on my standard epiphany. What does change there?

Neither are configurable at all, sorry. The reason that they cant be officially nicely integrated into epiphany with configuration options and all that is that they're hackish workarounds to bugs in gecko and xulrunner that won't be fixed until epiphany 2.20 comes out. I'll attach a version compiled without the tab changes in a few.

As for session saving, the only change is that it also save the session whenever epiphany is closed, not just when it crashes.

Sorry for the late reply and all that.

edit: I found some [packages put together by an epiphany dev]("http://diego.aureal.com.pe/archives/2006/11/30/epiphany-patched-packages-edgy/") that have most of the patches in my version and keep the standard tab behavior which should work. Oh, and glad you liked it, jon.

---

### Post by Jonathan Métillon on 2007-01-22
> **deadlydeathcone said:**
> As for session saving, the only change is that it also save the session whenever epiphany is closed, not just when it crashes.

Yes, I discovered that after. And ***that*** is a fantastic improvement!

> **deadlydeathcone said:**
> I found some [packages put together by an epiphany dev]("http://diego.aureal.com.pe/archives/2006/11/30/epiphany-patched-packages-edgy/") that have most of the patches in my version and keep the standard tab behavior which should work.

Thanks!

---

