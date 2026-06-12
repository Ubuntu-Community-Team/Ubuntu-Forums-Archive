---
title: "Install  error  on  D630"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by fsmfly on 2007-08-05
Hi,everyone
    I  have  xp  on my dell d630  and  left 20G for  ubuntu install.  But I have  a problem,  when I boot from the  live CD, it dump into  the BusyBox , the error in casper.log is :
     /init: /init :1: cannot open /dev/sda: No such file
     mount:Mounting /dev/sda2 on /cdrom failed: No such device
    stdin:error 0;
     Unable to find a medium containing a live file system.
sdaX  is  my  IDE disk  partitions,  I suspected  that maybe  my CDROM or IDE disk  have an error.   And I  cannot  find  scd  in  /dev.

So I take off  my  IDE  disk ,then boot the system from CD again, But it still dump into  the BusyBox, have the error msg in casper.log is :
      unable to find a medium containing a live file system. 
It seems have problem with CDROM

Then  I try  another method  that  install  ubuntu  from IDE not live CD ,  follow the instruction I set all  the config, restart  and choose  "ubuntu linux", it  seems have a  error and  ask me to have hardware diagnose, the diagnose error is that : IDE device failed, Black media or no media is present in optical driver,requires media with data.

I  have tested  the three   methods  above  on my asus  notebook PC , it   all  works well, So  I  am  every  confused  and ask  help here,   Thanks  a lot.

---

### Post by jsage on 2007-08-05
fsm,

the problem is well-known and has been discussed extensively on these forums (search on "D630").  You'll find the answer to your problem here:

[http://ubuntuforums.org/showthread.php?p=2996678#post2996678](http://ubuntuforums.org/showthread.php?p=2996678#post2996678)


have fun,
john

---

