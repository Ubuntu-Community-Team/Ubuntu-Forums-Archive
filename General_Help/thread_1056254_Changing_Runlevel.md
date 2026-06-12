---
title: "Changing Runlevel"
date: 2009-01-31
forum: General Help
---

### Post by magawake on 2009-01-31
I just installed 8.10 and it seems its missing /etc/inittab. From what I read, "upstart" has taken over the traditional /etc/inittab method. 

I would like to change my runlevel from 5 to 3 to disable automatic GDM. plus I am a CLI guy :-)

---

### Post by lswb on 2009-01-31
The default runlevel in ubuntu is 2 and 2 through 5 are all configured the same in a default installation. An inittab file can be used to specify a different runlevel, but little if anything else with the ubuntu upstart system.

See 
[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)
or
[http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html](http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html)

for more info.

---

