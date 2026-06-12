---
title: "GDM only displays background and mouse"
date: 2013-07-07
forum: Desktop Environments
---

### Post by smitty96 on 2013-07-07
Well, I've really run into a predicament this time. Haven't posted here in a while.. 'Spose that's a good thing, as far as having issues goes :).

I recently installed Ubuntu GNOME 13.04. Today I decided I'd update to GNOME 3.8. That went just fine, but certain changes made me want to go back. I used ppa-purge to remove the gnome3 and gnome3-staging PPAs, then removed their .list files manually from /etc/apt/sources.list.d/ because they were still there. (should they have been?)

And that's where the problems started. That removed **a lot** of packages, including gdm and gnome-shell. I tried installing ubuntu-gnome-desktop, but several of my packages were above the needed version. I downgraded all the dependencies that needed to be, and then installed ubuntu-gnome-desktop successfully. GDM is back, and it runs at startup, but shows nothing but my background and mouse. It also seems I don't have an /etc/gdm/gdm.conf. Is there a default file I could just copy there or is that not a problem? If it isn't that then I have no idea what the problem is :P.

Any help at all is appreciated!

[EDIT] Fixed it myself, actually just had to find the rest of the packages that were updated and downgrade them all. The script given [here]("https://help.ubuntu.com/community/DowngradeHowto") was a lifesaver.

---

