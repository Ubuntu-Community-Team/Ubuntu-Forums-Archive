---
title: "Beryl rotate cube--freezes computer"
date: 2007-05-05
forum: Desktop Effects &amp; Customization
---

### Post by rygar on 2007-05-05
Hi,

I just updated Beryl from 0.2.1 to 0.3.0 (using [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb))
so that i could use the widgets plugin on my screenlets

the widgets plugin works great, but unfortunately my rotate cube has some problems now!
i can rotate the cube fine (alt+ctrl+left/right) as well as unfold it (alt+ctrl+PgDn)

however, when i try to maneuver by mouse (ctrl+alt+button1), it doesn't work!  the cube shows up and i can rotate as much as i want, but as soon as i let go of the mouse button, on any workspace, it freezes!  i have tried desktop wall and desktop plane as well, and they don't work, but i figure they are less stable plugins.

any ideas?

thanks!
jeff

---

### Post by aidanr on 2007-05-05
submit a bug report [here]("http://bugs.beryl-project.org/"), it might be the same bug as [this]("http://bugs.beryl-project.org/ticket/1822") one?

---

### Post by rygar on 2007-05-05
yes, probably is the same bug.

like i said, it worked fine in 0.2.1 but not in 0.3.0, so i imagine that would help someone elucidate the bug

thanks again

---

### Post by rygar on 2007-05-05
for those of you who are having problems with this in 0.3.0, try downgrading to 0.2.1

a simple uninstall for me didn't work and i ended up having to manually delete beryl-related files and then track down dependencies.  but the point is, if you can fully uninstall 0.3.0 and then re-install 0.2.1, you can select the widget plugin from synaptic and then both widgets and cube rotating work fine.

hope this helps!

---

