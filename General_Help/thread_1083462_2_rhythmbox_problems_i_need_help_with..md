---
title: "2 rhythmbox problems i need help with."
date: 2009-03-01
forum: General Help
---

### Post by etherealeclipse on 2009-03-01
1. How do i get Rhythmbox to convert .ogg to .mp3 when transferring to my ipod.

It somehow could convert them to .m4a which didn't work on the ipod before , but after try fedora 10 and running back (on fedora 10 i got it to convert .ogg to mp3 that worked on the ipod), after coming back i can't get it to do either but prefare to get it to convert to .mp3.

(Solved) Recalled Sound Converter required a different ugly pack to convert files i.e. the multiverse version.

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

2. Rhythmbox crashes Totem.

When using rhythmbox totem crashes when opening but if i open totem first then rhythmbox totem works fine and both can play at the same time and fix for this i want to be able to just pause rhythmbox to use totem not close it.

Any help is appreciated. Thanks

---

### Post by Gramps on 2009-03-01
You probably need to add the codecs for mp3 and other non free codecs which are not included with Ubuntu.

The best way to do this is follow the directions on [Medibuntu]("http://www.medibuntu.org/")

I'm going to guess at this time you can't play mp3's with rhythmbox either, the above will fix that also.

---

### Post by etherealeclipse on 2009-03-01
Actually I can play mp3's thats the really confusing part cose all i did was install the 'ugly' pack in fedora 10 to get it to work.

---

### Post by etherealeclipse on 2009-03-01
bumb for the final problem.

---

