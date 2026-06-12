---
title: "Hibernate mode no workie, swap or free space?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by scottylans on 2006-06-25
My machines both won't hibernate (laptop and desktop)   comes up with a space error.


My swap space is only 256mb because I have 1gb ram in the desktop and 2gb in the laptop, I am a total n00b so I barely run ANY apps or backend stuff, so I figure I really don't need much swap space :(

My question is, to make hibernate work, do I need just enough hdd space free on the / partition or do I need a swap file the same size as my ram?

Anyone? (thanks)

---

### Post by blimpyboy on 2006-06-25
When hibernating the memory state is saved to the swap partition.  I don't know if this is adjustable.

---

### Post by scottylans on 2006-06-25
[QUOTE=blimpyboy]When hibernating the memory state is saved to the swap partition.  I don't know if this is adjustable.[/QUOTE]


>: ( DAMN!

You know, I swear it was hibernating on one of my installs which had a 256mb swap file :(

---

### Post by scottylans on 2006-06-25
[QUOTE=scottylans]>: ( DAMN!

You know, I swear it was hibernating on one of my installs which had a 256mb swap file :([/QUOTE]

Ok I've looked further into this and it is dependant upon swap space free AND amount of memory in use.

So if I boot a fresh copy of Ubuntu up, open NO applications and hibernate it works

If I open FF / a few apps it won't.

So I've made my swap 800mb - I'll never use that much ram as a dumbass user :)

---

