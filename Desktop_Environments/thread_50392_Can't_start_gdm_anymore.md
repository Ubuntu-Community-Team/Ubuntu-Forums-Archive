---
title: "Can't start gdm anymore"
date: 2005-07-20
forum: Desktop Environments
---

### Post by ubuntuuser on 2005-07-20
Hello guys,

this is a really strange error.
I am using Gnome. I was setting up my WLAN adapter, changed the WEP and clicked the OK-button. Then the system stopped suddenly, no more mouse movement, no switching to the console, nothing, not even HDD access. I waited some time but nothing happened so I had to cut off the power. I rebooted the computer, but gdm won't start anymore. During boot, it simply says "Starting gdm failed". When I log in as root and type "gdm", I get the following error message: 

```

Error while loading shared libraries: /usr/lib/libgtk-x11-2.0.so.0: invalid ELF header

```

I tried apt-get --reinstall install libgtk2.0-0, and what I got was
```

ldconfig: /usr/lib/libfontconfig.so.1.0.4 is not an ELF file - it has the wrong magic bytes at start.

``` 
I get the same error message with all of the following files:
```

libXft.so.2.11 
libpangox-1.0.so.0.800.1 
libpango-1.0.so.0.800.1 
libpangoft2-1.0.so.0.800.1 
libpangoxft-1.0.so.0.800.1 
libaudiofile.so.0 
libgamin-1.so.0.0.26 
libkrb5.so.3,2 
libdes425.so.3 
libgssapi_krb5.so.2 
libesd.so.0

``` 
Not that this was already enough, there also was

```

ldconfig: /usr/lib/libdes425-so.3 is not a symbolic link. 
ldconfig: /usr/lib/libgssapi_krb5.so.2 is not a symbolic link.

``` 
If anybody here has an idea what else I could try I would be very glad. I would really not like to reinstall the system, 'cause I have invested a lot of time to setup all the programs I need and to configure these properly.

Btw: how can I make an image of my root partition (it's /dev/hda7) that I can use in case something like this is going to happen again?

Thanks in advance.

---

### Post by debian_n00b on 2005-07-20
Maybe try booting with the following parameter:

ide=nodma


Would a reinstall of gdm help I wonder?



Heres a simple way to copy a partition bit for bit.


Code:

dd if=/dev/hda7 of=/home/user/backup.img 


To restore, it would be the reverse of above command. You just substitute the input file(IF) with the output file(OF)

dd if=/home/user/backup.img of=/dev/hda7


Also, you'll want to do this with the partition mounted read-only. And if home is on same partition, you will have to specify a diferent destination to copy the backup to.

---

