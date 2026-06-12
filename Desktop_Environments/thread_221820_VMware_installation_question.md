---
title: "VMware installation question"
date: 2006-07-24
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-24
I followed the instructions  [here]("http://ubuntuforums.org/showthread.php?t=183209") but when vmware console comes up - it is empty (look at the screenshot)
When I run it from the terminal this is what I get:

```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2) GTK Accessibility Module initialized *** glibc detected *** free(): invalid pointer: 0x0939bc78 ***
```



I dont know if it's related but I've been having problems with skype (unsolved yet) whenever I ran it I get a smilar error :

```

*** glibc detected *** free(): invalid pointer: 0x08a246a8 *** Aborted

```
Someone said it might be realted to SCIM , I wonder if anybody managed to run VMware alongside SCIM?

(screenshot can be found on a similar post I made [HERE]("http://ubuntuforums.org/showthread.php?p=1290819#post1290819") #339)

---

### Post by SnEptUne on 2006-08-14
Yes.  I can run vmware (vmware-server) even though I am using SCIM.  I don't think it is SCIM related at all.

You may try to replace the vmware's library with your local version with the following command:

```

sudo mv /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0.old

sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

If that does not work, try setting the environment variable VMWARE_USE_SHIPPED_GTK="yes".

In the worse case, you may set VMWARE_USE_SHIPPED_GTK="force".

---

