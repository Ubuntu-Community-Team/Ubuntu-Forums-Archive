---
title: "Beagle doesn't pick up changes in files"
date: 2009-04-29
forum: General Help
---

### Post by tbraun on 2009-04-29
Hello!

Beagle doesn't seem to detect changes in files for me. Almost as if it wouldn't use inotify. Changes only are accessible once these files have been re-indexed as part of regular index sweeps.

To test the whole thing, I created a very small text file in my home directory. It was part of the initial indexing run that Beagle did. Then, I added a small phrase to that file and searched for that phrase with Beagle. No match! With inotify it should have picked up the change and should have re-indexed it, but no such luck.

I also used 'inotifywatch' to make sure that inotify works for me at all (it does).

Any idea how long I should normally have to wait before Beagle will show changes to files in its results? I thought with inotify that would be more or less instantaneous. Is there some setting I have to do in Beagle to enable the use of inotify?

For what it's worth, I recently upgraded from 8.10 to 9.04.

Any help is greatly appreciated.

Thank you very much...

Tom

---

