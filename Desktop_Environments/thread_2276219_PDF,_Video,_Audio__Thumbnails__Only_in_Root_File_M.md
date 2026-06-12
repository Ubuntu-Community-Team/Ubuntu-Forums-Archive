---
title: "PDF, Video, Audio  Thumbnails  Only in Root File Manager"
date: 2015-05-01
forum: Desktop Environments
---

### Post by Gaylaird_Culbreth on 2015-05-01
Thumbs are working fine in root Caja or PcmanFM On Ubuntu 14.04.2  with  Mate. . Thumbs for  PDF, Video, Audio are not generated when running file manager unprivileged. Thumbs were working until today when I  installed/uninstalled OOO-Thumbnailer and cleared **"/home/user/.thumbnails"** and  **"/home/user/.cache/thumbnails"**. 

I deleted these folders, recreated them, chmod'ed them and disabled/renabled previews in my file managers -no joy. I reinstalled Atril, Totem, FFmpegthumbnailer, Thumbnailer service and all my Gstreamer plugins -no joy. I created a fresh secondary user profile  and still no thumbs on desktop or file manager  with regular user privileges.

Thumbnails for PDF, Video, Audio under  root Caja or PcmanFM work perfect. Under my regular privilege level thumb generation fail so bad  there isn't  even a **"/home/user/.cache/thumbnails/failed" **generated.

I think this is a bizarre permission problem. 

Please help. Thanks!

---

### Post by TheFu on 2015-05-01
Perhaps if you show the owners, groups and permissions for the directories and files?
I've never needed to use any GUI program with sudo. They often have strange side effects when used that way, since non-existent directories will be created as root, thus preventing normal users from editing or creating any new files in those directories.

So - cause the issue, post the permissions and we can move on from there.

---

