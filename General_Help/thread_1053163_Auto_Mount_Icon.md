---
title: "Auto Mount Icon"
date: 2009-01-28
forum: General Help
---

### Post by pasha07 on 2009-01-28
Hey guys, 

i am still new to ubuntu.. i need to add an auto mount icon (like the one for the windows partition) under "places" for a network hard drive?

I added to fstab but it mount everytime at start up.. i just want it to mount when i click the icon/bookmark/launcher... 

thanks,

---

### Post by drs305 on 2009-01-28
> **pasha07 said:**
> I added to fstab but it mount everytime at start up.. i just want it to mount when i click the icon/bookmark/launcher... 

thanks,

You can go back into fstab and add the following to the list of options:
```
users,noauto
```
Those two additions will allow any user to mount/unmount the device, and will prevent the device from automatically being mounted at startup or when the "sudo mount -a" command is run.

The edited line would look something like:
```

/dev/sda2 /media/mydata ext3 defaults,**noauto,users** 0 0

```

---

### Post by pasha07 on 2009-01-28
thanks a bunch for the reply. 

now i have 

//192.168.1.100/public/media/usr8700 cifs username=***,password=****,_netdev,uid=***,gid=users,noauto 0 0 

how do i add the icon under the "places" where "my computer" and "cd/dvd" are to mount it when i click it, since with the lines above, it doesn't mount and i don't have the icon. 

thanks again,

---

