---
title: "Updates to multiple machines"
date: 2005-01-07
forum: General Help
---

### Post by nocturn on 2005-01-07
I was curious (thinking of something).
What would be the best way to roll out updates to a number of Ubuntu boxes in a network?

I kow it would be possible to script apt using SSH.
But are there standard tools available for such a thing? 

Again, I'm just playing with thsi idea for now.

---

### Post by Juergen on 2005-01-07
You could search with synaptic (or pure apt) for apt, to see whats available :-)

You might be interested in 'apt-cacher' or 'apt-proxy'

I use 'apt-move' to create a local repository I can carry home on a CD.
At least this one isn't adapted to the different structure of the ubuntu-repository, so I suspect you have to tweak the other apt-'foo', too.

---

### Post by randy on 2005-01-07
You can do it using ssh but you could just setup your own mirror and use cron to pull updates at specified times.

---

### Post by nocturn on 2005-01-12
[QUOTE=randy]You can do it using ssh but you could just setup your own mirror and use cron to pull updates at specified times.[/QUOTE]


Thanks
This seems like a good idea and it can be done at install time so it should work.

---

