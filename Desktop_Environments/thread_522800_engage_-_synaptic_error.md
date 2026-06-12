---
title: "engage - synaptic error"
date: 2007-08-11
forum: Desktop Environments
---

### Post by adam_r on 2007-08-11
i'm tring to install engage via synaptic and it gives me this error:

[I]engage:
 Depends: libecore1-dbus  but it is not installable
 Depends: examine but it is not going to be installed[/I]

where do i get this libecore1-dbus?

---

### Post by kugn on 2007-08-11
you already have the correct repository?

see [http://elbuntu.org/](http://elbuntu.org/)

---

### Post by adam_r on 2007-08-11
still no good... i dont know what to do...

---

### Post by adam_r on 2007-08-11
still no good... i dont know what to do...

is there a way to force apt-get to skip one dependence?

---

### Post by kugn on 2007-08-12
well i've never found out a way to skip a dependency. and the reason why it's a dependency is cos the dependent package wouldn't work without being able to depend on a dependency :p

the reason why you could not install engage properly might be because engage is pretty much in a mess (from what i've read so far), if not an already abandoned project. the one functioning engage i've seen is in dreamlinux, a distribution based on debian etch. their engage is based on a very old version of it, but works pretty well. you could steal it from their repository, or the official enlightenment repositories for debian (which i think are better maintained because the developers use debian). but you are forewarned of any screwups due to installing debian stuff 

good luck :)

---

