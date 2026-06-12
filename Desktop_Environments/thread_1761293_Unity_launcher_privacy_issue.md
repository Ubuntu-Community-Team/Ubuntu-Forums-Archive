---
title: "Unity launcher privacy issue"
date: 2011-05-18
forum: Desktop Environments
---

### Post by b9k9kiwi on 2011-05-18
I quite like Unity, although I didn't expect that I would.

The launcher, however, has me a little concerned at present.

It functions perfectly well, but the Files & Folders object has as a feature a 'recent' section which displays recently opened files.  This is much the same as a menu object available in Gnome, except with the latter you could clear recent files for security or privacy purposes - you cannot do this in Unit.

I have found that if you drag a file from the 'recent' section in the Unity Files & Folders object to Trash it doesn't just delete the shortcut - it deletes the target as well.

It is not at all clear if and how you can configure the File & Folders and the Applications objects to display what you want rather than the default, and the inability to quickly and safely clear recently opened items is something I think is in need of a fix.

---

### Post by Copper Bezel on 2011-05-18
The Recent Documents support is handled by Zeitgeist, which only recently updated upstream with a blacklist manager. See _[here]("http://www.omgubuntu.co.uk/2011/05/activity-log-manager-for-zeitgeist-lets-you-blacklist-files-and-apps-delete-your-history-more/")_ for information and a PPA for the most recent version.

---

### Post by b9k9kiwi on 2011-05-18
Thank you for the pointer - I have installed the manager module which satisfies my needs.

---

### Post by djchandler on 2011-05-27
My solution: complete removal of Zeitgeist via Synaptic, especially since I have no need for Unity either.

Why do we need another tracking application? And is the end user the only one making use of Zeigeist's database?

Yes, I'm paranoid. But that was one of the reasons I started using linux.

Edit: Unity still works without Zeitgeist. No thanks to the PPA for a management application (or something like it) that *should* have been part of the the Zeitgeist package in the first place. How about a little disclosure? And I'll stick to the officially recognized and supported Ubuntu applications. All too often, third party software is the way windows installations get infected. This kind of opening is just right for a social engineering attack vector.

[http://ubuntuforums.org/showpost.php?p=10867866&postcount=4](http://ubuntuforums.org/showpost.php?p=10867866&postcount=4)

---

### Post by stinkeye on 2011-05-27
> **djchandler said:**
> My solution: complete removal of Zeitgeist via Synaptic, especially since I have no need for Unity either

Why do we need another tracking application? And is the end user the only one making use of Zeigeist's database?

Yes, I'm paranoid. But that was one of the reasons I started using linux.
Well that's the benefit of open source. 
If anything nefarious is going on you'll soon here about it.

---

