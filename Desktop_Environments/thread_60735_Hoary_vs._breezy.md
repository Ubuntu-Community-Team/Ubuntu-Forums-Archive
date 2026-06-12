---
title: "Hoary vs. breezy"
date: 2005-08-29
forum: Desktop Environments
---

### Post by snpz on 2005-08-29
Right now i use hoary, should i update my sources.list file to breezy and upgrade my system? AFAIK breezy is like unstable?

---

### Post by Kuolio on 2005-08-29
atm breezy is very unstable, wait for the release candidate (or what ever...), i heard that it's going to be released September 8th. Not sure though.

---

### Post by incinerator on 2005-08-29
[QUOTE=snpz]Right now i use hoary, should i update my sources.list file to breezy and upgrade my system? AFAIK breezy is like unstable?[/QUOTE]

If you have a question that is not specific to kubuntu, I'd appreciate if you'd post it to one of the other subforums.

---

### Post by snpz on 2005-08-29
Sorry, i posted and then only realized!:(
Next time i will post in correct place!;)

---

### Post by apokryphos on 2005-08-29
Actually, Breezy is reasonably stable at the moment, and a lot faster. It's worth trying out if you don't mind dealing with a few quirks.

---

### Post by Triton on 2005-08-29
...and what are those quarks?

---

### Post by daller on 2005-08-31
Hi there, I've been running Breesy Badger for a while now - and I haven't run into any problems at all... (less than I did in Hoary)

Go for it - but please don't modify your sources.list, and try to dist-upgrade - Most likely it will fail, leaving a broken system!

---

### Post by incinerator on 2005-08-31
[QUOTE=daller]Hi there, I've been running Breesy Badger for a while now - and I haven't run into any problems at all... (less than I did in Hoary)

Go for it - but please don't modify your sources.list, and try to dist-upgrade - Most likely it will fail, leaving a broken system![/QUOTE]
 Well, how else shall I upgrade my system, then? By downloading a colony cd and installing from cd? Bah, that's soooo 20th century...

---

### Post by earobinson on 2005-08-31
I have been only impresed in breezy (still a few bugs) eg (rhythmbox is broken right now) so if you need your computer working at %110 dont upgrade yet. but if your like me and can live with a bit of crap so you get the bleeding edge go for it.

cheers

---

### Post by celdar on 2005-08-31
[QUOTE=incinerator]Well, how else shall I upgrade my system, then? By downloading a colony cd and installing from cd? Bah, that's soooo 20th century...[/QUOTE]
 A couple weekends ago I changed "hoary" to "breezy" in my sources.list, and then did

apt-get update
apt-get dist-upgrade

And a few hours later I was running Breezy... more or less. That weekend was one of the big upgrade weekends, so several things in my upgraded system were broken (including gnome-panel). I have been running apt-get upgrade or apt-get dist-upgrade every day since then, and watching what gets fixed, and what stops working. Last weekend, rhythmbox broke (actually, I'm told it's a bug in the underlying GTK - sound-juicer and audigy are also broken, and the only CD-audio player I can get to work is goobox).

So, yes, thanks to the miracle of Debian, you CAN upgrade to Breezy with dist-upgrade.

But, since it's still in a huge state of flux, you may well end up with a broken system. Play at your own risk...

Bill

---

### Post by zugvogel on 2005-08-31
Is the new version of Ubuntu going to carry OpenOffice 1.0.4 or 2.0? I looked at distrowatch, but openoffice isn't even listed in the snapshot.

---

### Post by enceladus on 2005-08-31
[QUOTE=zugvogel]Is the new version of Ubuntu going to carry OpenOffice 1.0.4 or 2.0? I looked at distrowatch, but openoffice isn't even listed in the snapshot.[/QUOTE]

Kubuntu Breezy --> OO2.0

Cheers

---

### Post by incinerator on 2005-08-31
[QUOTE=celdar]A couple weekends ago I changed "hoary" to "breezy" in my sources.list, and then did

apt-get update
apt-get dist-upgrade

And a few hours later I was running Breezy... more or less. That weekend was one of the big upgrade weekends, so several things in my upgraded system were broken (including gnome-panel). I have been running apt-get upgrade or apt-get dist-upgrade every day since then, and watching what gets fixed, and what stops working. Last weekend, rhythmbox broke (actually, I'm told it's a bug in the underlying GTK - sound-juicer and audigy are also broken, and the only CD-audio player I can get to work is goobox).

So, yes, thanks to the miracle of Debian, you CAN upgrade to Breezy with dist-upgrade.

But, since it's still in a huge state of flux, you may well end up with a broken system. Play at your own risk...

Bill[/QUOTE]
 Ah, that sounds like debian unstable, only it really seems to be unstable *ggg*

---

