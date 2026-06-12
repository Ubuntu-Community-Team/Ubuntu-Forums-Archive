---
title: "How do I merge Firefox bookmarks?"
date: 2009-04-25
forum: General Help
---

### Post by xeddog on 2009-04-25
I have a dual boot computer with two different flavors of Ubuntu installed on separate hard disks.  Well, they're both on Jaunty now, but they were different.  Anyway, each installation had it's own Firefox and each Firefox had it's own bookmarks.  Many of the bookmarks are duplicated, but many are not.  But even the bookmarks that are duplicated may or may not exist in different folders within the main bookmarks.  Quite a mess really.

What I would like to do is a one-time merge of the bookmarks on /dev/sdb into /dev/sda.   I don't think I will need to keep the bookmarks on sdb because that disk will soon be given over to Karmic and will get formatted.  I don't really see anyway around some manual work to re-arrange them all if I can even get them merged into one place.  It's just getting them all into one place while eliminating the duplicates.

I have looked into bookmarkbridge mentioned in some threads, but that seems to only allow merging of bookmarks from different browsers within one system.  It would not let me merge from the other installation.

I also looked into XMarks (formerly Foxmarks) mentioned in a few other threads, but it seems to be quite a bit of overkill.  Plus it looks like it works by storing everything on a server somewhere.  I don't like putting any of my data on anyone else's server that I don't have to.  I'm not paranoid about that (yet) but I am working on it.  :)  I suppose I could do that though.  Nothing I have bookmarked is "sensitive" but it is the principle.

Any ideas???


TIA,

xeddog

---

### Post by coffeecat on 2009-04-25
If you don't mind the manual work - seems as though this is overdue anyway :wink: - one way would be to open one of the firefoxes, then, Bookmarks > Organise Bookmarks > Import and Backup > Export HTML.

Save/copy the HTML to wherever it can be accessed by the other firefox, close down, reboot into the other distro, open the other firefox and follow the same path, except choose Import HTML. You'll now have a right old mess to sort out, :p but since you're already in Organise Bookmarks, you're in the right place to do so. If you haven't come across it yet, the 'move' option in the 'Organise' (leftmost) menu is going to come in useful here.

By the way, the menu names in Organise Bookmarks might be different in Ubuntu - I'm in Vista atm :oops: so I'm reminding myself from the Windows Firefox which does have slight differences. But the Organise Bookmarks utility is laid out the same in Linux, Windows and MacOS - I'm sure of that because I often do something similar in all three OSs. Like you, I'm not prepared to leave details of my bookmarks on a distant server. I have nothing to hide in my browsing habits, but it is the principle of the thing.

---

