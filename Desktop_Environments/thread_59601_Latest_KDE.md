---
title: "Latest KDE"
date: 2005-08-24
forum: Desktop Environments
---

### Post by guitard00d on 2005-08-24
How long will it take before Kynaptic will pull down the latest KDE? It would be nice to be able to benefit from quite a few of the bug fixes in the current KDE. I know that I can modify my sources.list and pull it down right now, but the Kubutu systems that I am maintaining are used in a commercial production environment. So, I'd rather not bastardize things and break the distribution. That's why I'm wondering how long it'll take before Kynaptic automatically knows there's an update to KDE.

---

### Post by incinerator on 2005-08-24
[http://kubuntu.org/hoary-kde-342.php](http://kubuntu.org/hoary-kde-342.php)

---

### Post by guitard00d on 2005-08-25
Thanks, but I'm already well aware of that link. That link is precisely the reason why I included this in my original message:

[QUOTE=guitard00d]I know that I can modify my sources.list and pull it down right now, but the Kubutu systems that I am maintaining are used in a commercial production environment. So, I'd rather not bastardize things and break the distribution.[/QUOTE]

So, I guess maybe I should have asked when the repositories listed in the default sources.list in Kubuntu (the ones marked with a "main restricted") will realize that there is an update to KDE. Hopefully that's a little more accurate and to the point.

---

### Post by ltmon on 2005-08-25
Hi,

Kubuntu follows the Ubuntu release schedule, which dictates a new release every six months.  The next one is Breezy (5.10) which is scheduled for October.

In between releases no official updates are made unless they fix a major, major bug or a security issue.  Even then you would probably only get a backport bug fix rather than a new KDE version.

This means no new KDE until October.  The Kubuntu devs have indicated that they would be prepared to delay the October release to coincide with the release of KDE 3.5 if it is necessary.

Cheers,

L.

---

### Post by guitard00d on 2005-08-25
Very interesting, I'm trying to decide if I should look at this as good news or bad news. I guess it all depends on how reliable the Kubuntu upgrade from Hoary to Breezy is. Which is the lesser of two evils, adding the repositories to my sources.list so I can just get KDE 3.4.2 now, or upgrade to the Breezy release? Breaking things and being forced to rebuild any of these systems will not score me any points with anyone. I just know some of the problems we're having have been fixed in 3.4.2 and we need to upgrade, but I don't know how tempermental other parts of Kubuntu are about an  upgrade that doesn't come from "main restricted".

---

### Post by apokryphos on 2005-08-25
[QUOTE=guitard00d]How long will it take before Kynaptic will pull down the latest KDE? It would be nice to be able to benefit from quite a few of the bug fixes in the current KDE. I know that I can modify my sources.list and pull it down right now, but the Kubutu systems that I am maintaining are used in a commercial production environment. So, I'd rather not bastardize things and break the distribution. That's why I'm wondering how long it'll take before Kynaptic automatically knows there's an update to KDE.[/QUOTE]
It will hardly bastardize it if you put in the other repository. It's already available, 3.4.2, you just have to add the location. Hoary has already been released, so it can't re-come with Hoary, can it? :)

---

### Post by syntruth on 2005-08-25
If it's any consolation, I've upgraded to KDE 3.4.2 and other than issues with graphical artifacts with installed styles/windecs (which I've posted about) it has been solid and works fine on all apps.  ('Cept for kaffiene hogging CPU after closing, so I stopped using it, not that I watch a lot of videos on my work PC.  ;-) )

---

### Post by guitard00d on 2005-08-25
> Hoary has already been released, so it can't re-come with Hoary, can it?

Hmmm, my Hoary CD has 3.4.0 not 3.4.2....

---

### Post by apokryphos on 2005-08-25
[QUOTE=guitard00d]Hmmm, my Hoary CD has 3.4.0 not 3.4.2....[/QUOTE]
Yes, that's exactly what I said. Hoary came out with 3.4, so it can't be re-released to have 3.4.2 with it. But you can still upgrade.

---

### Post by guitard00d on 2005-08-25
Okay...I didn't say anything about re-relasing Hoary with 3.4.2, I was asking about the default repositories knowing there is an upgrade to KDE the same way they realize there are other updates. No problem, ltmon answered my question very accurately.

---

### Post by guitard00d on 2005-08-26
[QUOTE=syntruth]If it's any consolation, I've upgraded to KDE 3.4.2 and other than issues with graphical artifacts with installed styles/windecs (which I've posted about) it has been solid and works fine on all apps.  ('Cept for kaffiene hogging CPU after closing, so I stopped using it, not that I watch a lot of videos on my work PC.  ;-) )[/QUOTE]

Looks like I didn't get quite as lucky as you. Two friends of mine running Kubuntu also experienced the same results.

1. Kcontrol disappeared from the K-Menu as well as from the System sub-menu.

2. Kynaptic never recovers after installing anything. Meaning, it always stays in its grayed-out state after installing software.

3. Numerous pointless programs were installed as part of the KDE 3.4.2 update. What I mean by "pointless" is the number of duplicate-functionality programs. As in, is there any real reason to have three image viewers and six media players?

Oh well, I hope the Hoary to Breezy upgrade works out better and fixes the Kynaptic and Kcontrol problems.

---

### Post by f1dave on 2005-08-27
[QUOTE=guitard00d]

1. Kcontrol disappeared from the K-Menu as well as from the System sub-menu.
[/QUOTE]
It's not a problem, been covered on here several times to fix it.

[QUOTE=guitard00d]
2. Kynaptic never recovers after installing anything. Meaning, it always stays in its grayed-out state after installing software.
[/QUOTE]
Also, read the forums... use synaptic or apt-get.

[QUOTE=guitard00d]
3. Numerous pointless programs were installed as part of the KDE 3.4.2 update. What I mean by "pointless" is the number of duplicate-functionality programs. As in, is there any real reason to have three image viewers and six media players?
[/QUOTE]
I don't know, maybe to provide /choice/? Personal preference? What seems pointless to you is quite helpful for others.

Hope that clears some things up.

---

### Post by guitard00d on 2005-08-27
LOL!

Hell, judging by what you said (or what little you said), you could just save some time and say RTFM since your reply was about as informational as no reply at all. I guess I'm to assume that you aren't supposed to point out a problem in these forums unless it's never been mentioned before? FWIW, I am well aware of how to use apt-get and synaptic. Thanks, but no-thanks...

---

### Post by f1dave on 2005-08-27
Without getting into some silly argument, I was simply pointing out the fact that the problems you mention are easily fixed, and each has several threads covering it on this forum already. Just use that search function.

RTFM is always a good idea, but so is searching the forums before complaining.

---

### Post by Peferling on 2005-08-27
Manuals are of little use as when you're dealing with bleeding edge distros and upgrades.  Forums, wiki's and common sence are your guide otherwise.

This goes for all platforms, mac, wintel, and linux - for which I use all three.

Rules of thumb:

1. Never test on a dedicated work machine.  It's handy to have a dedicated test machine nearby to "try" new versions.  That way, if you experience a problem, it won't impact your production, (and reputation).

2. Never ever install or upgrade anything while in the middle of production or project.

3. Never allow a user with limited experience or access to attempt the fix/install themselves (unless it's their own personal machine and they are willing to accept the consequences).

4.  Always research for a simple fix, workaround or patch before diving head long, willy-nilly into a major upgrade/install.  There's great potential to create more problems/issues than the fix itself.

Anytime you violate these rules, and the fix works in your favor, then consider yourself lucky.  These are the hard lessons I've learned in my dual role as an IT/Multimedia developer guru.

Pete

---

