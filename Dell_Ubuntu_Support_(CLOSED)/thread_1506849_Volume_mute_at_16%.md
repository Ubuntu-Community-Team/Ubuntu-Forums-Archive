---
title: "Volume mute at 16%"
date: 2010-06-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gruppler on 2010-06-10
The volume keys all work just fine on my Dell Inspiron 6400, but when the volume is less than 17%, the sound is completely mute. I've looked for places to configure this and searched other forums and haven't found a solution.

Playing with alsamixer reveals some strange behavior. I see two volume bars, Master and PCM. PCM is at or near 100%, and Master is usually near 10%. When I change the volume via any gnome interface (volume keys, cairo-dock widget, etc.) both bars move; PCM moves slightly between 98% and 100%, and Master moves more drastically between 0% and 100%, but it moves much more slowly as the volume gets higher.

Now, if I lower PCM to, say, 50% and raise Master to 100% using alsamixer, and then change the volume again with gnome, both bars jump back to the same positions as before.

Any ideas?

---

