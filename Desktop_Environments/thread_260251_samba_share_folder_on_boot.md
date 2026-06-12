---
title: "samba share folder on boot"
date: 2006-09-18
forum: Desktop Environments
---

### Post by hraposo on 2006-09-18
I want mount a samba share folder on boot. I add this line to fstab ```
//helder-desktop/helder /media/samba smbfs noauto,users,username=helder,passwd=123123 0 0
``` But this line don't mount the folder on boot.  I must do:```
#mount /media/samba
``` How knows wat is wrong in fstab line?

---

### Post by hraposo on 2006-09-18
Maybe the problem is in the **user**. In user I use the login name...

---

### Post by infoseeker on 2006-09-18
As a start, the 'noauto' option prevents any partition from mounting at boot
Take a look here -->
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by hraposo on 2006-09-18
Problem solved!
I add **mount -a -t smb** to /etc/rc.local and works fine!

---

### Post by tagra123 on 2006-09-18
Rather than using fstab

Try this

from a terminal 

```
sudo mkdir /media/samba-helder
sudo gedit /usr/bin/connectshares
```

add the following contents to the file:

```
#!/bin/bash

# syntax (SAMBA SHARE)
# mount -t smbfs //remote-server/somesharedfolder /media/somesharedfolder-comp1 -o username=remoteusername,password=remotepassword

#example (SAMBASHARE)
# mount -t smbfs //192.168.1.25/shares /media/somesharedfolder-comp1 -o username=remoteusername,password=remotepassword

mount -t smbfs //helder-desktop/helder /media/samba-helder -o  username=helder,passwd=123123
```

Save the file.

Make the script executable:

```
sudo chmod +x /usr/bin/connectshares
```

execute (test the script) from a terminal

```
sudo connectshares
```

This script should have mounted your remote shared folder.

To execute this script at startup (AUTOMOUNT)

PANEL MENU: System > Preferences - Sessions

Click on Add

For Startup Command type in /usr/bin/connectshares

Click on OK

Restart the computer and the folder should be mounted.

The script makes it handy to mount automatically if the remote computer is already running, especially if there are several shares to mount. If the other computer wasn't on this script can be run after it is turned on.

---

### Post by stanna on 2008-02-21
that worked for me perfectly  tagra123, thanks mate

---

