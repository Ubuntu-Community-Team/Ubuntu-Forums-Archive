---
title: "Accessing  Windows shares"
date: 2009-07-18
forum: Desktop Environments
---

### Post by Ekeluo on 2009-07-18
This is the situation: I can login to gnome on my system, (the wifi connects automatically) and by just opening nautilus and clicking the network places icon, access windows shared files from an XP home laptop elsewhere in my house. I can't do this if I login to kde 4.2.96 on the same computer (same wifi connection). Dolphin only shows me my shared printers, as does nautilus. Any help will be appreciated.

---

### Post by Ekeluo on 2009-07-18
Come on? Pretty please everyone? :mad:

---

### Post by Zorael on 2009-07-19
Odd. What happens if you connect to the machine via its ip?
```
dolphin smb://<*ip.to.XP.machine>*
```
Unless you've installed and set up WINS resolving of computer names, you can't access it via smb://<*computer name>*, though that's easy enough to fix. It should still pop up under network shares, though.

---

### Post by Ekeluo on 2009-08-05
Haven't been using kubuntu recently, got a new PC with vista for first time. Updated it it SP2 and quite frankly, it isn't nearly as bad as people seem to make it out to be.  Moving on...

In process of updating my system to 4.3.0, logged in to ubuntu right now and just now discovered that samba is not installed. Should be able to give you a response by tonight. Thanx.

---

### Post by Ekeluo on 2009-08-10
Sorry for taking 4 days when I said I'll reply tonight, had a few connection and configuration issues. Now running kde 4.3 tho.

It seems it's just a problem of not discovering devices properly; typing the address works fine (this is  a different system than I initially started the thread on, but problem's the same). Accessing files is ok, but it doesn't list the computers by name. Yet to see if nautilus still does.

P.S. Do you know which of synaptic | songbird | kget | firefox 3.5 | dolphin is dependent on python. When running all at once, I notice that whenever songbird switches tracks (the song notifier add-on is installed; now disabled as suspect in crime case) the system pretty much hangs for some minutes (anything from 4-10 or more). Really bleeding annoying.

Info: just typed the i.p address in the location bar and it worked.

---

### Post by slakkie on 2009-08-10
Put something like this in your /etc/fstab file

```

\\samba-server-name\share /path/to/mount/point  cifs uid=wesleys,gid=root,credentials=/home/your_user/.smb,iocharset=utf8,codepage=unicode,unicode,auto 0  

```

If you don't want the share to be mounted automaticly set noauto instead of auto.

If you connect to a workgroup/domain, add the following sniplet to the mount options:

```

workgroup=name_of_domain_or_workgroup

```

/home/your_user/.smb looks something like this:
```

username=your_user_name
password=the_password

```

This will make sure you can mount everything whatever GUI you are using.

---

### Post by slakkie on 2009-08-10
> **Ekeluo said:**
> 
P.S. Do you know which of synaptic | songbird | kget | firefox 3.5 | dolphin is dependent on python. When running all at once, I notice that whenever songbird switches tracks (the song notifier add-on is installed; now disabled as suspect in crime case) the system pretty much hangs for some minutes (anything from 4-10 or more). Really bleeding annoying.

apt-cache rdepends python

---

### Post by Ekeluo on 2009-08-10
> **slakkie said:**
> Put something like this in your /etc/fstab file

```

\\samba-server-name\share /path/to/mount/point  cifs uid=wesleys,gid=root,credentials=/home/your_user/.smb,iocharset=utf8,codepage=unicode,unicode,auto 0  

```

If you don't want the share to be mounted automaticly set noauto instead of auto.

If you connect to a workgroup/domain, add the following sniplet to the mount options:

```

workgroup=name_of_domain_or_workgroup

```

/home/your_user/.smb looks something like this:
```

username=your_user_name
password=the_password

```

This will make sure you can mount everything whatever GUI you are using.
Thanks Slakkie, but I don't think that's what I want. Also, the computer isn't always available (an msi wind some rooms away, gets turned off occassionally), I'm quite satisfied with the way nautilus does things. I just want dolphin to query available computers and shares on the network like nautilus does so I don't have to type the IP address. I'll try making a link to it, see if it works. Thanks

Later: Link works, but opens new windows. Hmmm...

---

### Post by Zorael on 2009-08-11
Computer "names" aren't resolved unless you install the **winbind** daemon (package of the same name) and enable *wins lookup*. See [this post](http://ubuntuforums.org/showpost.php?p=6316236&postcount=8).

If you want to *mount* a share, you could try **smb4k**. It's pretty neat.

Alternatively, **smbnetfs** or **fusesmb**, though I find them to be unstable. Those two will mount the whole "computer neighborhood" (or whatever the Windows term is) into a directory, from which you can then browse by workgroups, then by computer, then by shares. But again, they crash.

---

