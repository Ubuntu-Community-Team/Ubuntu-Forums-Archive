---
title: "TinyFugue"
date: 2010-05-14
forum: Gaming &amp; Leisure
---

### Post by pokebirdd on 2010-05-14
I guess this is sort of more like a bug report but I'm not quite sure if I should file one so I'm posting on the forums instead.

Anyways, I just wanted to say that the tinyfugue reps are a bit out of date. If you "sudo apt-get install tf", it installs version 4.0 by default which is really old. To install version 5.0, you have to "sudo apt-get install tf5". Perhaps we could change it so that the default tf package automatically installs tf5?

Again, I'm not really sure if I should be filing a bug report for this. :confused:

---

### Post by OliW on 2010-05-14
I would guess the reasoning for this is that the 5.0 client is a beta and beta-state packages don't usually replace stable release packages. There are, of course, dozens of exceptions to this but most people prefer a stable release with (where applicable) the option for a beta version under a different package name.

If you want to get it replaced, go upstream and kick somebody hard and get them to push out a new stable release. It's been at 5.0b8 for well over three years with little response to bug reports so I can only assume the project maintainer has lost interest.

---

