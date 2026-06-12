---
title: "Kde 4.0.1"
date: 2008-02-01
forum: Desktop Environments
---

### Post by puelocesar on 2008-02-01
KDE 4.0.1 is now tagged for release, anyone knows when it will be on repositories? I have 4.0.1 on other machine and it's much more stable than 4.0.0

---

### Post by stikonas on 2008-02-01
We can guess that this can happen on Wednesday.

---

### Post by shafin on 2008-02-01
What are the changes?

---

### Post by samwyse on 2008-02-01
[http://www.kde.org/announcements/changelogs/changelog4_0to4_0_1.php](http://www.kde.org/announcements/changelogs/changelog4_0to4_0_1.php)

---

### Post by puelocesar on 2008-02-01
> **stikonas said:**
> We can guess that this can happen on Wednesday.

Something special about wednesday? Like THE day of updating things :P

---

### Post by Erunno on 2008-02-01
> **puelocesar said:**
> Something special about wednesday? Like THE day of updating things :P

No, not to my knowledge. Usually there's a period of one week between tagging and announcement to give distributions time to build their packages and translators to prepare the announcements.

---

### Post by Cyrus XIII on 2008-02-02
While those 4.0.x releases may only be intended for bugfixes, it's sort of a bummer that they apparently didn't include "fixes" for some of the more glaring Plasma vs. Kicker regressions, (panel placement and resizing, show desktop, multi-row and desktop-dependent taskbar, and so on), even though many of them have already been implemented. The worst thing the devs could "break", by keeping monthly feature updates for Plasma coming until 4.1, is people's reluctance to use that baby on a day-to-day basis.

---

### Post by samwyse on 2008-02-03
[http://vizzzion.org/?blogentry=806](http://vizzzion.org/?blogentry=806)

Maybe the patch above was too late for 4.0.1 or it just wasn't listed. I guess changing the colour is still missing.

The new Gwenview is currently very limited, though it does have crop and resize unlike the old one.

---

### Post by Cyrus XIII on 2008-02-03
Yeah, I read this one too. Panel resizing would probably have come too late for the 4.0.1 tagging, but the multi-row taskbar was already mentioned in the January 27th Commit-Digest.

[http://commit-digest.org/issues/2008-01-27/](http://commit-digest.org/issues/2008-01-27/)

---

### Post by puelocesar on 2008-02-04
> **samwyse said:**
> [http://vizzzion.org/?blogentry=806](http://vizzzion.org/?blogentry=806)

Maybe the patch above was too late for 4.0.1 or it just wasn't listed. I guess changing the colour is still missing.

The new Gwenview is currently very limited, though it does have crop and resize unlike the old one.

You don't need to change the color, the taskbar renders a SVG, so you just need to change the SVG for a better one :) 

I did this and now is very beautiful. well, I updated and recompiled my Kde4-svn on my testing Arch Linux and I can resize, and configure plasma taskbar, and after changing the SVG my kde-svn desktop is very very nice to use..

My only problem is that on my work I have a not-too-fast celeron machine and it would be painful to run the automated compilation script for building kde4 while running Rails with Mongrel, firebird, postgresql and programming on Netbeans, so I depend on Kubuntu builds, that are very buggy.. :(

---

### Post by samir85 on 2008-02-05
4.0.1 is in the repositories now. However during the update process ktorrent-kde4 somehow became uninstalled :(

---

### Post by stikonas on 2008-02-05
I have looked at the dependencies. it depends on libgif4 (should be no problem in Hardy), not on libungif4 (which is default in Gutsy). It tries to uninstall even more packages on my system (ffmpeg, emacs, imlib, ktorrent and a few others).

**Edit:** It seems that this bug is fixed.

---

### Post by jlacroix on 2008-02-05
For some reason, after I upgraded to 4.0.1, most of my KDE4 apps no longer work. When I click on the KDE4 versions of Konsole, Ksysguard, system settings, or Konqueror (and a bunch more) they appear for a brief second then disappear. Am I the only one?

---

### Post by HotShot on 2008-02-06
No! It also happens to me. All KDE4-Apps are gone ... :(

```
Setting up konsole-kde4 (4:4.0.1-0ubuntu2~gutsy1~ppa1) ...
```
But
```
$whereis konsole-kde4
konsole-kde4:
$konsole-kde4
bash: konsole-kde4: command not found

```

I use this repository 
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

I think we have to wait

---

### Post by samwyse on 2008-02-06
I did a quick test. The KDE4 apps are now in /usr/lib/kde4/bin/. They start normally from KDE4 run dialog, konsole launches the kde4 konsole and so on. In KDE3 you have to use the full path.

Is it just me or is thumbnailing worse than in KDE3? It's slow especially going back and forward from a folder.

---

### Post by jlacroix on 2008-02-06
I figured out the problem.

The commands for KDE4 apps were sufficed with "-kde4". This is how they are supposed to be, so you can run for example "konsole" to start the KDE3 version of Konsole, or "konsole-kde4" to start the KDE4 version of Konsole.

Now, this is broken and the suffixes were removed. So "konsole" starts the KDE4 version wihle logged into KDE4, and the konsole-kde4 icon is broken in KDE3.

Repeat that for all of the KDE4 apps.

Nice one Kubuntu!!! I can't believe they didn't bother to test this!!!! Seriously, that would've been a very hard bug to miss!

In 4.0.1 the kmenu is still completely broken for me with almost no icons other than question marks in the menu.

---

### Post by CupofDice on 2008-02-07
With kde 4.0.1 I have this weird problem with konqueror opening tabs instead of staying in the same tab. I also can't login to ubuntuforums.org, keepassx.org, and I assume other sites. I get a html page instead. Makes it pretty much unusable for any serious browsing. Anyone else having this problem. This is on a fresh install, and I had the same problem before I reinstalled.

[[IMG]http://b.imagehost.org/t/0067/snapshot1.jpg[/IMG]](http://b.imagehost.org/view/0067/snapshot1.png)

Other than that I am loving kde4, especially after more than 2 years of seeing gnome go nowhere (also had a stint with fluxbox). I use to not like kde for all the regular reasons, but kde4 seems to be fixing that for me. I could do with a bit more options though, but I will stay patient for them to come. The fact that dolphin can do pretty much everything of importance that nautilus could do and more in just the short period of development time (compared to nautilus) and that [Gentle Gnome]("http://www.gnome-look.org/content/show.php?content=31128") (the greatest mockup ever) has been ignored shows me that gnome is going nowhere.

---

### Post by Cyrus XIII on 2008-02-07
I think Dolphin is still -the- killer app of KDE4 (its KDE3 backport notwithstanding). I had friends who run Windows see it in action and they immediately wanted a file browser with twin view and another friend, who is quite a Mac OSX fan told me that he considers Dolphin's feature set superior to that of Finder - nice.

By the way, why exactly do need two repositories with KDE4 for Gutsy? There is the one at [http://ppa.launchpad.net/kubuntu-members-kde4](http://ppa.launchpad.net/kubuntu-members-kde4), which is still not authenticated and then there are (somewhat outdated) packages in backports.

---

