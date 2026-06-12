---
title: "NTFS Trash problem"
date: 2008-04-29
forum: Desktop Environments
---

### Post by manro on 2008-04-29
Every time I try to delete a file from a NTFS partition I receive the following message: "Cannot move file to trash, do you want to delete immediately? The file 'xxx' cannot be moved to the trash."  Is there any fix/patch/workaround for this issue?  Thanks! MaNRo

---

### Post by gigenieks on 2008-06-10
I have exactly the same problem.

How can i fix this? Is there something with permissions wrong? :confused:

---

### Post by manro on 2008-06-10
> **gigenieks said:**
> I have exactly the same problem.

How can i fix this? Is there something with permissions wrong? :confused:

Take a look at the **#4** post on this post:
```
[http://ubuntuforums.org/showthread.php?t=804083&highlight=ntfs+trash](http://ubuntuforums.org/showthread.php?t=804083&highlight=ntfs+trash)
```Hope it helps :)

---

### Post by kaibob on 2008-06-10
Duplicate post removed by Kaibob

---

### Post by kaibob on 2008-06-10
> **manro said:**
> Take a look at the **#4** post on this post:
```
[http://ubuntuforums.org/showthread.php?t=804083&highlight=ntfs+trash](http://ubuntuforums.org/showthread.php?t=804083&highlight=ntfs+trash)
```Hope it helps :)

The post cited by manro--which I wrote under a previous user account--no longer works reliably. I played around with this a bit and found the following:

* After making the suggested changes, the deleted file is correctly moved to the trash folder, and there is no longer a warning dialog.

* Initially, the trash icon does not indicate that it contains a deleted file, but when I click on the trash icon it changes to reflect the deleted file.

* I am able to remove the deleted file from the trash by selecting the right-click option to "empty trash." However, the trash icon still indicates that there is a deleted file in the trash, although another click on the trash icon changes it to reflect that the trash is empty.

I have my trash icon in a panel only. Perhaps a trash icon on the desktop works properly.

The trash in Hardy is undergoing substantial change--perhaps it is best to leave things as they are until this is sorted out by the developers.

---

