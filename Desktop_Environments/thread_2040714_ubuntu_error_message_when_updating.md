---
title: "ubuntu error message when updating"
date: 2012-08-11
forum: Desktop Environments
---

### Post by oren tal on 2012-08-11
whenever I chck for an update I get the following error message:
```
W:Failed to fetch http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```


Howcan I fix this?

---

### Post by drs305 on 2012-08-11
The server may just be down temporarily. You can disable the 'cheleb' listings for now by unticking them in the Other Sofware tab of Software Sources:
```
gksu software-properties-gtk
# After closing Software Sources, run:
sudo apt-get update
```
You can try to enable it later if it was just offline. The second command should update the repository list. If you still get an error there may be one of the ppa listing you missed.

---

