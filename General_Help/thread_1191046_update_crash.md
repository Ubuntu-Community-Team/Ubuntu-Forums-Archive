---
title: "update crash?"
date: 2009-06-18
forum: General Help
---

### Post by nutu on 2009-06-18
hi,

i updated my ubuntu with the update manager , and right after the update was complete i had noticed that it was if my ubuntu had been reinstalled.

i am running ubuntu 9.0.4. in virtualbox 2.2.0. using a windows host OS. the problem is that after the update my sharedfolder (which i configured to load automatically on startup) no longer is seen in ubuntu (luckily i have it backed-up), as well as the mouse integration does not work anymore (i have to press ctrl to get between the two OSs). 

does anybody have any idea what happened? how cna i fix this? system restore or something? 

:confused:

---

### Post by MyR on 2009-06-18
sounds like you need to install guest additions

peace

---

### Post by nutu on 2009-06-18
> **MyR said:**
> sounds like you need to install guest additions
 
peace
 
 
EDIT: running guest additions worked fine and everything is back to normal (ie mouse, automatic loadup sharedfolder). thank you for your help. it still puzzles me that updating my system caused this to happen though. is it normal for guest additions to be 'uninstalled?' if thats the right term to use, and need to be reinstalled like that? any reason why all of this happened? i've updated my system plenty of times but it is the first time that this hs happened. pleae let me know for future references. thank you again for your help.

---

### Post by MyR on 2009-06-18
Not sure what would cause them to be uninstalled either.  Perhaps you reverted to an earlier snapshot/state.  Glad I could help!

---

