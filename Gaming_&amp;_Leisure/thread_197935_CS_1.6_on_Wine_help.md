---
title: "CS 1.6 on Wine help"
date: 2006-06-16
forum: Gaming &amp; Leisure
---

### Post by mrmustardman on 2006-06-16
I cant seem to get CS 1.6 to work on Wine. I cant even get Steam to install... 
I need somebody to take me through this.
I have Wine installed already. I know it works because IE 6 and WMP work.
I can get through the steam installation, but once its done, it wont load, and wont ask for my username and password. 

anyone help?:confused:
i used the wine tutorial here : [http://www.ubuntuforums.org/showthread.php?t=14958](http://www.ubuntuforums.org/showthread.php?t=14958)

---

### Post by echo $USER on 2006-06-16
[QUOTE=mrmustardman]I cant seem to get CS 1.6 to work on Wine. I cant even get Steam to install... 
I need somebody to take me through this.
I have Wine installed already. I know it works because IE 6 and WMP work.
I can get through the steam installation, but once its done, it wont load, and wont ask for my username and password. 

anyone help?:confused:
i used the wine tutorial here : [http://www.ubuntuforums.org/showthread.php?t=14958](http://www.ubuntuforums.org/showthread.php?t=14958)[/QUOTE]

use this one instead; worked for me

[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

---

### Post by mrmustardman on 2006-06-16
i tried what u said before you edited it, and it worked better... now it says : 
"Fatal Error: Could not load module "bin/vgui2.dll"

---

### Post by echo $USER on 2006-06-17
did you load the mozcontrol and add the tahoma font?  have you installed hardware accelerator for video?

---

### Post by nanophobic on 2006-06-17
Hi, I have a bit different kind of question.

I dual boot on windows and linux(ubuntu dapper). I already have a steam installation on a FAT32 partition that lies in between the windows ntfs partition and the linux partitions. 

Would I need to make a fresh install of steam on my linux partition as well? Or can I just use the existing installation in the FAT32 partition?

---

### Post by monstrebu on 2006-06-17
I have my steam installation on a fat32 too. Only install the steam on wine and copy the folder "SteamApps" where are located the "gcf's" and your account files/folder to your wine/steam folder. It worked for me.

---

### Post by nanophobic on 2006-06-17
[QUOTE=monstrebu]I have my steam installation on a fat32 too. Only install the steam on wine and copy the folder "SteamApps" where are located the "gcf's" and your account files/folder to your wine/steam folder. It worked for me.[/QUOTE]

Thanks! I would try that out and share the results :)

---

### Post by eqisow on 2006-06-17
> i tried what u said before you edited it, and it worked better... now it says :
"Fatal Error: Could not load module "bin/vgui2.dll"

Take a look at [this thread]("http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=1917&forum=10").

---

