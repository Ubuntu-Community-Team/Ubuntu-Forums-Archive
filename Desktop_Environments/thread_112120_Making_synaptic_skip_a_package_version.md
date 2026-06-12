---
title: "Making synaptic skip a package version"
date: 2006-01-03
forum: Desktop Environments
---

### Post by sander marechal on 2006-01-03
Hello,

I was wondering how I can make synaptic (and thus the update notifier) skip a certain version of a package. I get my Wine packages from the Wine-HQ repository. Wine 0.9.3 was great. The current version 0.9.4 broke Internet Explorer though. This will be fixed in Wine 0.9.5. 

I have a .deb file for Wine 0.9.3. I would like to remove 0.9.4 and install 0.9.3 in such a way that Synaptic/Update Notifier will disregard Wine 0.9.4 from the Wine-HQ repository. However, they should upgrade/notify when Wine 0.9.5 comes out.

How can I accomplish this? Many thanks!

--
Sander Marechal

---

### Post by dcstar on 2006-01-04
[QUOTE=sander marechal]Hello,

I was wondering how I can make synaptic (and thus the update notifier) skip a certain version of a package. I get my Wine packages from the Wine-HQ repository. Wine 0.9.3 was great. The current version 0.9.4 broke Internet Explorer though. This will be fixed in Wine 0.9.5.

I have a .deb file for Wine 0.9.3. I would like to remove 0.9.4 and install 0.9.3 in such a way that Synaptic/Update Notifier will disregard Wine 0.9.4 from the Wine-HQ repository. However, they should upgrade/notify when Wine 0.9.5 comes out.

How can I accomplish this? Many thanks!

--
Sander Marechal[/QUOTE]
Install the version you want (the new Wine stuffed me up too!), select the installed package in Synaptic, and then do Package-Lock Version.

Those packages will then be marked as "Pinned" in the Status area, and you won't be prompted to upgrade them.

---

### Post by sander marechal on 2006-01-04
Thanks!

BTW, I e-mailed the Ubuntu/Debian package maintainer and he gave me this download link to get the 0.9.3 debs. Hope this solves it for you too!

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803)

---

