---
title: "Only some thumbnails show after upgrading to 24.04"
date: 2024-09-09
forum: Desktop Environments
---

### Post by lister171254 on 2024-09-09
Files V46.2 on Ubuntu 24.04 does not generate thumbnails for mp4 files after upgrading from a previous version of Ubuntu. 

I have ffmpegthumbnailer installed and this worked prior to the upgrade.
I have deleted the fail, large and small folders from .cache/thumbnail, which is how I found this issue

I’ve also upgraded one of my laptops and found a similar issue, only this time it’s the .avi files that don’t have a thumbnail. 
I’ve deleted everything under the thumbnail folder and noticed that only the ‘large’ folder is created when I open the folder that contains the videos

I’ve finally deleted the thumbnail cache completely, but when I open Files/Nautilus, they are still there (i.e., they don’t get generated). So the question is now, where are the thumbnails if they are not in .cache

---

