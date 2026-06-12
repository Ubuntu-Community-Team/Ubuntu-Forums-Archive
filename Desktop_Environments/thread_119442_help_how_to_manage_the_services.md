---
title: "help: how to manage the services?"
date: 2006-01-19
forum: Desktop Environments
---

### Post by jason2005 on 2006-01-19
I used redhat for years and switched to ubuntu recently.  I'm trying 
to find out how can I manger the services. I want to find out how to:

1.  list the services that is on by default
 
under redhat , to find service that default on on level 3, I could 
   chkconfig |grep '3:on'  

how to do that in ubuntu. update-rc.d seem unable to 

2.  I try to manaully turn on remote vnc servers ( not through GUI) 
what's the package I need, and how to find where is the configuration files.

3. what is the equivalent of redhat's command in ubuntu/debian
/sbin/chkconfig , /sbin/service ?

thanks in advance. 

Jason

---

### Post by Turin Turambar on 2006-01-19
There's a program in "System/Administration" called Services. But you can also install BootUp-Manager for even more options.

---

### Post by jason2005 on 2006-01-19
thanks. Turin.

 I search through synaptic,  I didn't find "Services", but a 
"sysvconfig" that contain /usr/sbin/service.   so is there another
program/package that would give me /sbin/chkconfig or equivillent? 


[QUOTE=Turin Turambar]There's a program in "System/Administration" called Services. But you can also install BootUp-Manager for even more options.[/QUOTE]

---

