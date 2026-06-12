---
title: "root windows partition access priorities"
date: 2005-12-24
forum: Desktop Environments
---

### Post by ESPOiG on 2005-12-24
i have finally got my windows partition to be mountd at startup... but now i cant access it unless i go gksudo nautilus * i think that is it :D... but how do i fix it so i can access it without having to go into the root controlled nautilus

---

### Post by NewbieNik on 2005-12-24
[QUOTE=ESPOiG]i have finally got my windows partition to be mountd at startup... but now i cant access it unless i go gksudo nautilus * i think that is it :D... but how do i fix it so i can access it without having to go into the root controlled nautilus[/QUOTE]

What happens if you try to access it as non-root? Is it a permissions error? If so try setting "Everyone" as read permission on your windows drive.

---

### Post by ESPOiG on 2005-12-24
tryd that it dont work i cant set permissions with root access on my windows partition as for accessin it with non-root permissions it just say 'you do not have permission to veiw/access this stuff' i just closd the window so i sorta forgetd wat it said but u get the gist of it :D... thx

---

### Post by NewbieNik on 2005-12-24
[QUOTE=ESPOiG] i cant set permissions with root access on my windows partition [/QUOTE]

You need to be booted in Wndows and then add "everyone" to the permissions tab, remember to set it as read-only though and bear in mind this does give EVERYONE permission to view that drive, so if your wireless make sure you're secure!!!

---

### Post by ESPOiG on 2005-12-24
k ill do it later it takes a while to shutdown and boot windows, then boot bak into breezy :D... thx man hope it works

---

### Post by annex on 2006-01-03
I found using the method in the ubuntu guide worked for me.  Just add the options to your fstab if you want it to be permanent:

[http://www.ubuntuguide.org/#mountunmountntfs]("http://www.ubuntuguide.org/#mountunmountntfs")

My appropriate line from fstab is:
/dev/hda2       /media/hda2     ntfs    iocharset=utf8,umask=000        0       0

---

