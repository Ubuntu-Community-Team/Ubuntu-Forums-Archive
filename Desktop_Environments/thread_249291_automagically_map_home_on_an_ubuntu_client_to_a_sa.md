---
title: "automagically map /home on an ubuntu client to a samba share"
date: 2006-09-02
forum: Desktop Environments
---

### Post by neill on 2006-09-02
hi

i have an fc5 fileserver serving mixed XP and ubuntu clients in a simple workgroup (ie **no **PDC or AD)

fc5 supports CIFS but not smbfs

each user on an ubuntu client has an account on the fileserver with the same username/password combo as their own client account and hence a /home/user on the server

i want the ubuntu clients to automount/map (whatever the correct term is) the client /home to the appropriate /home/user on the server - this needs to happen at logon and transparently to the user

hence users can do whatever they want with /home and it's actually on the server (where **I** can back it up :) )

i'm confused reading all the various autofs howtos and all about pam, winbind etc etc - principally i'm not sure which applies to me ](*,) 

can anyone come up with a simple solution to this ?

thanks

neill

---

### Post by pwrstick on 2006-09-05
Does this thread help?
[http://ubuntuforums.org/showthread.php?t=248656]("http://ubuntuforums.org/showthread.php?t=248656")

I used this to automatically connect to a samba share, but I'd imagine you would do the same thing in fstab that I'm doing.  my fstab ended up with a line like this:

//192.168.1.123/sharedfolder /mnt/netshare smbfs username=bleh,password=bleh,dmask=777,fmask=777,auto 0 0

---

