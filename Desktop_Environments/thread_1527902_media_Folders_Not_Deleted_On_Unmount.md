---
title: "/media Folders Not Deleted On Unmount"
date: 2010-07-09
forum: Desktop Environments
---

### Post by phetus on 2010-07-09
Hello. I am having a problem with auto-generated folders for external UMS devices in the /mount directory not being deleted once unmounted (using Safely Remove Device). They will become locked by the system and undeletable giving an 'in use' error when attempted. This does not occur on every unmount, but approximately 25% of the time, and I am unable to determine the reason for this quondam error as opposed to the correct folder deletion. The next time the same device is mounted, the system will create a new folder with a NAME_ pattern. Rebooting the system will release these remaining folders from system use, and are then deletable. The problem is not dependent upon the specific external device, as this has occurred with several different UMS devices. 

This problem has developed after the upgrade to 10.04 Lucid (fresh install), and did not occur on any previous version of Ubuntu.

If anyone has any idea what could solve this problem I would be very thankful!

---

### Post by fredknex on 2010-08-24
I am having this problem also (again).

its happened in the past, and i ended up just doing a clean install to fix it.

"sudo rmdir" can usually delete the empty folders, but its a pain to do this constantly. the old media folders keep my filepaths from being correct, as then to mount my drive it creates a new folder, "drive_" or "drive__" and so on.

---

