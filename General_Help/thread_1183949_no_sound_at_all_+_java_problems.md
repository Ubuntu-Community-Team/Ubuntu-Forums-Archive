---
title: "no sound at all + java problems"
date: 2009-06-10
forum: General Help
---

### Post by amiacamal on 2009-06-10
i have no sound on my laptop at all. its dual booted with vista and i have sound on vista, so i know the speakers aren't broken.. also i cant get sun java installed. i was told to use "sudo apt-get install sun-java6-jre sun-java6-plugin" it worked on my old laptop about a month ago, bun now it wont install it for me.

---

### Post by doas777 on 2009-06-10
try this:
```
sudo apt-get install ubuntu-restricted-extras
```
that will get you java, flash, acrobat and a bunch of codecs, filters, plugins, and loaders.

who knows, may fix your sound as well/

---

### Post by michy99 on 2009-06-10
> **doas777 said:**
> try this:
```
sudo apt-get install ubuntu-restricted-extras
```
that will get you java, flash, acrobat and a bunch of codecs, filters, plugins, and loaders.

who knows, may fix your sound as well/

I don't think java is included in ubuntu-restricted-extras any more.

---

### Post by michy99 on 2009-06-10
> **amiacamal said:**
> i have no sound on my laptop at all. its dual booted with vista and i have sound on vista, so i know the speakers aren't broken.. also i cant get sun java installed. i was told to use "sudo apt-get install sun-java6-jre sun-java6-plugin" it worked on my old laptop about a month ago, bun now it wont install it for me.

What errors do you get when you run the apt-get command?

---

### Post by amiacamal on 2009-06-10
java command working again... im confused... oh well. anyone got a sound solution? it takes me ages to answer cos my internet connection is so slow i coukd actually cry...

---

### Post by doas777 on 2009-06-10
> **michy99 said:**
> I don't think java is included in ubuntu-restricted-extras any more.

didn't know that. 'twould be a shame. I was thinking it at least had IcedTea (which seems to be pretty good).
I usually get a sun jre along with my jdk, so I'm not sure I ever looked to see which version was in use.

---

