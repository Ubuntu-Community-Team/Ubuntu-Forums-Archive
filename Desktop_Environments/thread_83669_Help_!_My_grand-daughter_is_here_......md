---
title: "Help ! My grand-daughter is here ....."
date: 2005-10-29
forum: Desktop Environments
---

### Post by AMD64_N_Linux on 2005-10-29
Help ! My grand-daughter is here and I have given her, her own Linux account. I let her log in, so she can play for a while at PBS Kids.org, or Nick jr.com, but there is a problem.

All of the icons on her desktop, specifically those that are links to the different partitions. I have assigned her a normal user account, but I have allowed access to all of the partitions by normal users, I think.

Is there a way to remove the icons to the other partitions from her desktop, so that I dont have to worry about her accidently deleting, moving, files or entire partitions. Can I just delete the icons, or is there a command, and which directory would I need to be in to run it, to remove the links to those partions.

Is it even possible? 

I hate to be in a rush, but she is here now, and I would really like to let her get on the PC.

Thanks for any and all help.


Edit,,, Thanks anyway, found it over here [http://www.ubuntuforums.org/showthread.php?t=81134&highlight=icons+desktop+partitions](http://www.ubuntuforums.org/showthread.php?t=81134&highlight=icons+desktop+partitions)

Thanks anyway and again.

---

### Post by clearnitesky on 2005-10-29
Yeah, just remove the links from her desktop. She has her own home folder and settings so nothing she does can affect your account in any way. 

Also, you can't delete partitions and stuff on Linux, it's just not possible unless you're logged in as root and start  doing really really stupid things. The last time I checked Ubuntu wont even let you log in as root unless you've set a password for it. 

That's one of the great things about Linux, normals users can't break it if they try because of the way every file you have is allocated an owner and read/write/execute permissions.

---

### Post by linuxlizard on 2005-10-29
Go to your menubar 
Applications- System Tools- Configuration Editor

Inside the configuration editor you want to open

apps- nautilus- desktop

uncheck the boxes especially computer icon and volumes

best

---

