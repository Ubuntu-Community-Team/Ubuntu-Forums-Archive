---
title: "Nicotine mixes up search results"
date: 2006-04-05
forum: Desktop Environments
---

### Post by Ian Maxwell on 2006-04-05
I have been running the Soulseek client Nicotine for several weeks now with no problems. Today, it just closed out of the blue. Since that point, there is apparently some confusion with searches--they are showing up in the wrong boxes. (That is, a search for "foo" will also give me results for "bar" and "baz" if I've searched for them at some point in the past.)

The only recommendation I've been able to find is erasing everything in ~/.nicotine, which hasn't helped; nor has a complete remove and reinstall via Synaptic. I assume some file Nicotine leaves laying around has gotten corrupted, but I don't know what it might be... does anyone else?

---

### Post by bionnaki on 2006-04-05
the version of nicotine in the repos sucks.
download the latest (1.0.8-e): [http://thegraveyard.org/daelstorm/nicotine-patch.php](http://thegraveyard.org/daelstorm/nicotine-patch.php)

just extract & modify whatever icon you have for nicotine to point to the "nicotine" python file in the new directory. if the file opens up as text file, then just make it executable.

no need to delete your old .nicotine directory - just keep it around but run the python file thats in the new directory.

---

