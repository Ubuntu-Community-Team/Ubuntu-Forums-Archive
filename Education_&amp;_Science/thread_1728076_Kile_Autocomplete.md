---
title: "Kile Autocomplete"
date: 2011-04-13
forum: Education &amp; Science
---

### Post by Faoesch on 2011-04-13
I'm a student at a university and I'm using kile to take my notes. When I used it yesterday everything worked perfectly well and in the evening I saw that it was the KDE Release Day 4.6 ([http://www.kubuntu.org/news/kde-sc-4.6](http://www.kubuntu.org/news/kde-sc-4.6)) and so I installed it with the ppa.

When I tried to use it today there wasn't any kind of auto completion in kile. So I restarted my laptop and tried it again. I looked in the settings for auto completion and there wasn't anything wrong either.

So know I'm left with kile which doesn't have auto complete.

Thanks for any kind of help :)

Edit:
Having searched for 1 second on Google I found this: [http://eumenidae.blogspot.com/2011/01/kile-kde-46-and-autocomplete.html](http://eumenidae.blogspot.com/2011/01/kile-kde-46-and-autocomplete.html)

---

### Post by pooja on 2011-05-08
I have the same problem. Is there a fix? 
Kile doesn't have autocompletion.

---

### Post by kinemagician on 2011-05-14
Go to 
Settings->Configure Kile-> Editing-> Auto Completion

Set Enable Auto Completion

---

### Post by fabio.hipolito on 2011-05-24
Hi,

I think the problem is related to version of kile in the repository of Ubuntu 11.04, namely the 2.0.85 beta4, which for some reason seams to b e broken, see:
[launch pad 1]("https://bugs.launchpad.net/ubuntu/+source/kile/+bug/778505");
[launch pad 2]("https://bugs.launchpad.net/ubuntu/+source/kile/+bug/777728");
[launchpad 3]("https://bugs.launchpad.net/ubuntu/+source/kile/+bug/772631").

Therefore > Settings->Configure Kile-> Editing-> Auto Completion might not solve the problem.

I solved the problem by upgrading to kile to version 2.0.86 beta6, you can find builds by [Philip Mu&#353;kovac]("https://launchpad.net/~yofel") here (introduce the ppa to wour list and get always the lastest build):

[for i386]("https://launchpad.net/~yofel/+archive/backports/+build/2489577")

[for amd64]("https://launchpad.net/~yofel/+archive/backports/+build/2489576")

Best regards.

---

