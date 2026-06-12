---
title: "Disappearing symlinks"
date: 2009-06-12
forum: Desktop Environments
---

### Post by jhetrick62 on 2009-06-12
I have a small server built on 8.04 lts and it runs zoneminder  besides some ftp work and a desktop for the primary user.

I added a 500gb hd to store the 8 cameras that we will be recording. The zoneminder is installed right from the standard ubuntu repos and is verision 1.22.3 and the box is fully updated.

When I added the new HD, I mounted it to /storage as it's just for 30 days of camera pic storage.  I then moved all zoneminder data files and used ln -s to create softlinks from the original file desinations to the new ones as zm didn't like just re-defining them in the software and would not replay events.  The original program files still exist on /usr/share/zoneminder.

My problem is that to overcome one other problem, I added the following symlinks onto the new drive.  
```
ln -s /storage/zoneminder/events/2 /storage/zoneminder/events/0295_back
```
This created a link in /storage/zoneminder/events that reads "0295_back -> /storage/zoneminder/events/2"

The problem that I have it that link disappears!  Definitely not there when I log back in.  I attempted to create a hard link but it claims that it's not allowed in the directory?  Mind you /storage is the mount point for the new HD (/dev/sdb1) so all other OS software including zm in located on primary drive /dev/sda1.  I know that you can't create a hard link to direct to another device.  

I also created this symlink using sudo as the current sub-directory, events, is controlled by www-data, the zm user for file storage.  I did attempt to chown the symlinks to www-data, but it would not allow that and continued to be root:root.

Any help on how to accomplish this without the symlinks disappearing would be greatly appreciated as they are needed for remote event file exporting.  The php script looks for the files based on the camera name, which in this case is 0295_back.

Thanks,
Jeff

---

