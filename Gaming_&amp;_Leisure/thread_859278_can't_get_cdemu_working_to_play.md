---
title: "can't get cdemu working to play"
date: 2008-07-14
forum: Gaming &amp; Leisure
---

### Post by duott on 2008-07-14
hello, i could use some help to get CDemu working to play. i'm running hardy x64, and i've installed all the packages from the repository with apt-get.

when i'm trying to load an mdf/mds image, i get:

```

$ sudo cdemu load 0 mycd.mds

ERROR: Failed to load image: org.freedesktop.DBus.GLib.UnmappedError.MirageErrorQuark.Code233492491: No parser can handle given image.
```

mds support is actually listed on the project site so it should handle it... when i start the daemon in a new terminal window, it seems to be working:
```

$ sudo cdemud

Starting daemon locally with following parameters:
 - num_devices: 1
 - ctl_device: /dev/vhba_ctl
 - audio_backend: (null)
 - audio_device: (null)
 - system_bus: 0
```

and when i try to load the image again in a separate window, the daemon says: 

```
cdemu0: __mirage_disc_mds_parse_sessions: failed to parse track entries!
cdemu0: __mirage_disc_mds_load_disc: failed to parse sessions!
```

Any suggestions?

Thanks

---

### Post by duott on 2008-07-14
it seems that after all it wasn't a cdemu problem since another mds mounted ok. 

can't find where i can delete this post though : )

---

### Post by hiippari on 2008-07-19
No, it is a CDEmu problem, because I get the exactly the same error when I try to load an .iso file that works just fine with the *mount -o loop* command.

---

### Post by jakswa on 2009-04-14
I just wanted to say I ran into problems with CDEMU and mdf images, too.

I even tried mdf2iso with no success.


My eventual solution was to use iat (sudo apt-get install iat) to convert my mdf/mds image to ISO:

iat original.mdf newfile.iso

and it worked!

---

