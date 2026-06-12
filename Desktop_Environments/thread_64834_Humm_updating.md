---
title: "Humm updating?"
date: 2005-09-12
forum: Desktop Environments
---

### Post by paperless on 2005-09-12
I heard something about 5.10 Breezy badger is it really just a preview or the final?

Can i update my hoary hedgehog?

---

### Post by Perfect Storm on 2005-09-12
The final is ready in a month.
The preview is there to correct (hopeful) the last bugs and test it overall and yes you can upgrade to breezy, just add the breezy repo. and disable the hoary repo. but beware that can happen some complications.

If I was you I'll wait one month and burn breezy. It's much safer.

---

### Post by celluloid on 2005-09-12
[QUOTE=paperless]I heard something about 5.10 Breezy badger is it really just a preview or the final?

Can i update my hoary hedgehog?[/QUOTE]
 5.10 Breezy Badger is still in heavy development. It is only a preview available so far.

It is possible to update your 5.04 Hoary Hedgehog via either an apt-get dist-upgrade or by download a colony cd. I believe colony 3? may be wrong.

To update your Hoary install you need to edit your /etc/apt/sources.list file and replace all mentions of 'Hoary' with 'Breezy'. Make sure not to change the ##Backports section (if you use these) as there are no backports for breezy and you will just get an error also don't change the first line where it mentions your CD, unless ofcourse you have the Breezy cd, but then you wouldn't need to do this. ;)

Once you've done that simply open a terminal and

sudo apt-get update
sudo apt-get dist-upgrade

There are a few interactions needed. Then restart.

I don't think it's possible to downgrade back to Hoary? (if anyone could confirm this) so if there are any problems, bugs or what not you will have to fresh install Hoary again. May be risky, but Breezy does have some very nice new features.

I reccomend you search the forums for further information though.
There is also some information on this at [www.ubuntuguide.org](www.ubuntuguide.org) i belive.

Hope this helps.
Grant.

---

