---
title: "lgeneral, lgc-pg and case sensitivity"
date: 2006-07-28
forum: Gaming &amp; Leisure
---

### Post by mcvos on 2006-07-28
I installed lgeneral, no problem. Finding lgc-pg was tricky (it was not in the same section as lgeneral for some obscure reason), but a good reason to try out Synaptic's search feature.

However, now that I'm trying to install the pg-data (got it from [http://lgames.sourceforge.net/index.php?project=LGeneral]("http://lgames.sourceforge.net/index.php?project=LGeneral"))
it turns out that lgc-pg expects uppercase, and pg-data contains lowercase filenames.

So how do I do this? Is there a version with uppercase filenames? Is there some option for lgc-pg to make it case insensitive? Am I doing it all wrong?

---

### Post by mcvos on 2006-07-30
Does nobody here know about lgeneral?

I've already tried writing a script that renames all the files to uppercase (although I think renaming shouldn't be necessary), but apparently it was too long ago that I wrote shell scripts regularly.

---

### Post by toxicduck on 2006-08-02
You can put lo2hi (inside archive) in ~/.gnome2/nautilus-scripts and then in nautilus right click a file or group selection of files choose scripts then lo2hi. You could also use ```
./lo2hi file1 file2 file3
``` hi2lo does the opposite thing (makes filenames all lowercase).

---

### Post by mcvos on 2006-08-06
Thanks, that helped. Although it looks like the original campaign is still not there.

---

