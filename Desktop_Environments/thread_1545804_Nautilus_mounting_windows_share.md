---
title: "Nautilus mounting windows share"
date: 2010-08-04
forum: Desktop Environments
---

### Post by zexelon on 2010-08-04
I have been looking into how to get Nautilus to emulate the windows "map network drive" feature.

I have found several howto's that use various command line utilities to try to do this, however they tend to be like trying to use a sledgehammer to fix small dents. 

When I connect to a share server, Nautilus puts a directory on my desktop that only Nautilus seems to be able to see and use. I would like to be able to access this directory with non-Nautilus applications.

Thanks for any help.

---

### Post by mikewhatever on 2010-08-04
You can use the address of that share/directory, which should be something like the following, smb://share_name. You can find out the exact address by opening the share in Nautilus and hitting ctrl+l. The address bar will appear, showing the address.

---

### Post by Morbius1 on 2010-08-04
> **zexelon said:**
> When I connect to a share server, Nautilus puts a directory on my desktop that only Nautilus seems to be able to see and use. I would like to be able to access this directory with non-Nautilus applications.
This is actually a cruel joke by the developers of this feature. When you use nautilus to access a remote share it actually creates a real mount point in an unconventional place:
> /home/your_user_name/.gvfsIt's the ".gvfs" part that may be a problem for you and your applications because it's a hidden directory.

To see it in Nautilus : Edit > Preferences > Views > Show hidden and backup files

To see it in your application, let's use Firefox as an example:
File > Save page as > right click an open space on the "Save As" dialog box > select "show hidden files".

---

### Post by lunatico on 2010-08-04
> **zexelon said:**
> I have been looking into how to get Nautilus to emulate the windows "map network drive" feature.


I'm looking for a similar thing. What I want is to be able to run \\server\share and have it automatically translated to smb://server/share

I was thinking a script that would take the path as a parameter, modify it and run it. But maybe there's a better way.

---

### Post by Morbius1 on 2010-08-04
> **lunatico said:**
> What I want is to be able to run \\server\share and have it automatically translated to smb://server/share

```
 gvfs-mount smb://server/share
```

---

### Post by lunatico on 2010-08-04
> **Morbius1 said:**
> ```
 gvfs-mount smb://server/share
```

Right but that just mounts the share to nautilus right? I don't see the point, if I just run smb://server/share from 'run application' (Alt+F2) it mounts the share and opens nautilus...

I was thinking on how to easily use a \\server\share path and have it converted to smb:// path and opened in nautilus...

---

