---
title: "Kde Kontact/Kmail -&gt; what's the best way to retrieve mail/notes from a dead system?"
date: 2011-11-29
forum: Desktop Environments
---

### Post by TomB19 on 2011-11-29
I left KDE about a year ago when akonadi stopped working on my system.  It took about a week of trying everything I could find on the web before I left it for dead.  I've never had a good experience with akonadi but I could get it to work by deleting the config directory every week or two in the early days.

My thought was to convert to Gnome but I never really got into it and have been using Windows 7.

Anyway, now I need some information from the notebooks in Kontact and I'd like to retrieve my old mail.  There is a lot of both.

To that end, I installed Kubuntu 11.10 this evening.  When I try to start Kontact, it fails with an Akonadi error.  It's a fresh install with hard disk format.  I swear, I've never seen akonadi run properly since it was introduced and I've put a lot of time into Arch and Kubuntu in the last several years.

I've killed the config directory a couple of times (.local/share/akonadi) but nothing seems to be working.

I'm not interested in wasting too much time because I can just write a python script to re-animate the mail and re-send it to my Windows Live Mail in an evening.  If it's easy, I might put an hour or two into getting the mail system up long enough to liberate my mail through the interface.

My main concern is the notebooks.  Where are they?  I don't care about the formatting, I just want the raw text.  There is a lot of important information in there that I realize I desperately need.  I'm willing to invest a couple of weeks recovering it.

Any help would be appreciated.  Thank you.

---

### Post by TomB19 on 2011-11-29
I've answered my own question.

The notebook data is under .kde/share/apps/kjots in a bunch of files.

Unfortunately, the stand alone Kjots won't work since akonadi isn't working, but I can harvest the data with a text editor and put it into something reliable, like maybe some LibreOffice documents.

I hope this helps someone else who is pinned down with akonadi errors.  :cool:

---

### Post by TomB19 on 2011-11-30
I'm embarrassed to admit I didn't think of searching for the data with grep until just now.  It took a long time to scrub through my home drive but the data was found at .kde/share/apps/kjots and .kde/share/apps/kmail/mail.

It looks like it's been over a year.  These file dates are from 2009.

You know, akonadi wouldn't be all bad if it worked.  At least it doesn't store data, only metadata, according to the various web sites that recommend different ways to repair it.

Perhaps one day.  :)

... but I'll probably be using Windows 14 by then.  :)


PS - here's a decent akonadi blog that explains what it's all about.

[http://techbase.kde.org/Projects/PIM/Akonadi#Post_KDE_4.5_.2FAkonadi_1.4](http://techbase.kde.org/Projects/PIM/Akonadi#Post_KDE_4.5_.2FAkonadi_1.4)

---

