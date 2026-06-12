---
title: "X-server crashing on boot after kernel update"
date: 2007-09-06
forum: Desktop Environments
---

### Post by jeepfreak2002 on 2007-09-06
I'm so freakin frustrated.  I had Edgy running my nVidia 7600 GT fine and was happily playing Guild Wars each night.  A "recommended upgrade" installed and now the x-server crashes on boot up.

I had installed Envy to get the most updated drivers running on the machine and now I'm screwed.  I've just spent an hour trying to reconfigure the x-server using the  "sudo dpkg-reconfigure xserver-xorg" which has worked in the past, but none of the settings that I set seem to work.

I'm at my wits end.  I don't even know how to export any errors because I can't get into a graphical interface to post.  Any help would be greatly appreciated.

---

### Post by thelocust on 2007-09-06
If you upgraded with envy there should be a backup. Boot up in Recovery Mode and enter

```
cd /etc/X11

ls
```

---

### Post by jeepfreak2002 on 2007-09-06
ty for your reply.  I continued to fiddle with the x-server settings and got Gnome up.  I then uninstalled the nvidia drivers through Envy and then rebooted and reinstalled the nVidia drives.  I'm back up.  If anyone reads this thread - use the vesa driver - not the nvidia driver w/ the bare minimum settings to get back into the GUI and the repair though Envy.  There is just something about the unsupported drivers that gets PO'ed everytime an upgrade installed.  Apparently the video driver are going to be better supported in Gutsy, though - God I hope so!

---

### Post by 20dollagi on 2007-09-18
Thanks jeepfreak!  I ran into the same issue after messing around with automatix, not realizing that everything was already set up.  Anyway, I'm back up, so thanks again.

---

### Post by dondad on 2007-09-20
> **jeepfreak2002 said:**
> ty for your reply.  I continued to fiddle with the x-server settings and got Gnome up.  I then uninstalled the nvidia drivers through Envy and then rebooted and reinstalled the nVidia drives.  I'm back up.  If anyone reads this thread - use the vesa driver - not the nvidia driver w/ the bare minimum settings to get back into the GUI and the repair though Envy.  There is just something about the unsupported drivers that gets PO'ed everytime an upgrade installed.  Apparently the video driver are going to be better supported in Gutsy, though - God I hope so!


If you install the drivers with Envy or from the website, it will break every time you get a kernal upgrade.

---

