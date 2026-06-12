---
title: "pmount is there but cant access floppy"
date: 2005-11-12
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-12
everytime i try to acces to floppy from nautilus it sends a message like this

Imposible to mount the volume selected

and in details says

UDI inserted is not a mountable volume

i had this problem backguards and i solve it installing pmount

now pmount is there but still the samething, the funny thing is that im able to formatt diskettes.

any suggestion


10x in advanced

---

### Post by futz on 2005-11-13
This isn't a real fix, but it will get your floppy mounted so you can use it. Type this in a terminal:
> mount /media/floppy0

---

### Post by futz on 2005-11-13
[QUOTE=mxyzptlk]any suggestion[/QUOTE]
Here's the proper fix. Be sure to disable that Dapper repository (as it says in one of the messages in this thread) after getting the pmount update installed. 
[http://www.ubuntuforums.org/showthread.php?t=88000&highlight=pmount+dapper](http://www.ubuntuforums.org/showthread.php?t=88000&highlight=pmount+dapper)

---

