---
title: "cairo-dock and open gl"
date: 2009-11-18
forum: Desktop Environments
---

### Post by tons-of-funs on 2009-11-18
i was just wondering if there was a way i could have cairo-dock start with the open gl, i have tried doing glx-dock and cairo-dock -o in the start up but it doesnt work. any help? thanks

---

### Post by fabounet on 2009-11-19
cairo-dock -o 
is the command you have to use.
be sure it is not launched somewhere else by the session.

---

### Post by tons-of-funs on 2009-11-19
i tried that and its not working, i went into system>preferences>start up apps>add new start up then for the program i tried cairo-dock -o and its not starting up

---

### Post by mCion on 2009-11-19
Do you have an entry in "startup applications" that opens cairo dock without open GL?

for me I could not just uncheck it, **I had to delete the entry** and then make a new one with Open GL.

Good luck..

---

