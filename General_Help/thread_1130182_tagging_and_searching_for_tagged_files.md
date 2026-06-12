---
title: "tagging and searching for tagged files"
date: 2009-04-19
forum: General Help
---

### Post by TurboFreak on 2009-04-19
hi,

i would like to tag my files so I'm able to search for content.

I tried out the tool tracker-tag but now I'm stuck with the attempt to search for files that match multiple tags.

Example: I want to find files that are tagged with Tag1 AND Tag2 (they may be tagged with more tags, too).
But i don't want to get files that are only tagged with Tag1 but not with Tag2 or vice versa.

Does anyone know how to tell this tracker-tag or maybe an alternative tool?

---

### Post by tehowe on 2010-08-01
> **TurboFreak said:**
> hi,

i would like to tag my files so I'm able to search for content.

I tried out the tool tracker-tag but now I'm stuck with the attempt to search for files that match multiple tags.

Example: I want to find files that are tagged with Tag1 AND Tag2 (they may be tagged with more tags, too).
But i don't want to get files that are only tagged with Tag1 but not with Tag2 or vice versa.

Does anyone know how to tell this tracker-tag or maybe an alternative tool?

I've been searching online for over an hour now, looking for whether there's a way to use boolean operators in the tracker tool, tracker-tag, or even in Nautilus CTRL-F with the bolt-on tracker functionality.

tracker-tag uses an implied OR operator as far as I can tell, this is the only mentiopn of multiple tags (from tracker-tag --help)

> To add, remove, or search for multiple tags at the same time, join multiple options, for example:

  -a TAG -a TAG -a TAGOkay... so if I run 

> tracker-tag -s internet I get a bunch of news items on net issues I've saved for research.

If I run > tracker-tag -s militarization I get a bunch of militarization news items I've saved for research 

But > tracker-tag -s militarization -s internet returns all of the above, which is the opposite of what I'd like to see.

In Nautilus, I can search on > tag:internet to look for one tag but don't see a way to do a more advanced search.

Is there a command line workaround? Or any gui that might handle this? Thanks.

---

