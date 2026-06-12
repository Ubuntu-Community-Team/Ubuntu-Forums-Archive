---
title: "How do I allow my other users access to sound"
date: 2006-08-17
forum: Desktop Environments
---

### Post by threethirty on 2006-08-17
The other people on my system are really angry, I'm the only one that has any sound.  When I login as them the volume indicator has the circle and slash, no symbol.  When I look at the the sound preferences it says that there isn't a sound card.

any ides?

---

### Post by Ramses de Norre on 2006-08-17
Are they in the audio group?
To give them permission to everything you've got permission for, do this:
```
for GROUP in `groups`; do sudo adduser username $GROUP; done
```
Change username to the right name.

You then might want to remove them from some groups again (the one which has the same name as your username, admin ...)
To do so: ```
sudo deluser username group
```

---

