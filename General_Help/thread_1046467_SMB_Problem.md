---
title: "SMB Problem"
date: 2009-01-21
forum: General Help
---

### Post by xeddog on 2009-01-21
I have a disk that I mount on my Ubuntu Intrepid system using SMB that I have a problem with.  This disk is located on a Digitech HDX-1000 networked media tank.  The HDX gives me the option of using nfs or SMB and I have chosen SMB because it is MUCH faster on my system.  

Anyway, using the Ubuntu file manager I can move files onto the drive, delete them, rename them, etc.  But the problem I am having is that I cannot EXTRACT files onto it.  I have a .rar file that I am trying to extract onto the HDX, but when I try, I get a permissions error.  I have set all of the appropriate permissions on the HDX as 777 for now until I can figure this thing out.  I can do all of the other functions from file manager, why can't I extract to it????

xeddog

---

### Post by LowSky on 2009-01-21
its a gnome glictch. you can try using the /media mount point instead of the SMB network mount point, tha might work as a workaround.

Otherwise whatever program your using for extraction you might need to run as root.

---

### Post by xeddog on 2009-01-21
I'm not quite sure I understand what you are saying ( I am still pretty new at this).  If I use the /media mount point, wouldn't that be a nfs mount instead of a SMB mount???  I have tried mounting the disk using nfs but the performance is horrible.  When I try to copy two files at the same time, I may as well go out for a while because the system will be totally unuseable until the copies are done.  CPU utilization is constantly in the high 90's to 100%.  And they take a lot longer than SMB.  With SMB, I have had 4 copies going at the same time and was at least able to still use the system.  Very sluggish, of course, but still useable.  This is why I want to use SMB.

As for the extraction program, I am using the default archive manager that gets installed with Ubuntu.  Nothing fancy.  I think the actual program is called "file-roller" and when I try to run it in a terminal window as root, it cannot see the smb share at all.

Thanks,

xeddog

---

### Post by danwood76 on 2009-01-21
The problem is with unrar as opposed to permissions.
Ive never been able to unrar over a network.

---

