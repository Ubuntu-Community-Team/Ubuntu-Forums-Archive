---
title: "SeamlessRDP with Windows 2008 r2"
date: 2010-06-16
forum: Desktop Environments
---

### Post by Malamut on 2010-06-16
I need to allow users to launch some published applications via RDP from Windows Server 2008. Now I use SeamlessRDP mode for it. But there is a two problems with it in Ubuntu:

1. There is a bug in Ubuntu patch to debian rdesktop package, so each seamless window has two borders - one from metacity, and one from Windows. So I already install rdesktop from lenny - it hasn't such bug.

2. I can't run explorer.exe. Windows taskbar doesn't appear in Ubuntu when I run explorer via seamlessRDP. Both with Ubuntu and Debian rdesktop packages. And I don't know workarounds for this bug.

So if anobody can tell something about seamlessRDP in Ubuntu - it will be great.

---

### Post by ykorman on 2010-08-15
Hi Malamut,
I'm afraid I can't help you, but I would appreciate you explaining how you've managed to configure Windows Server 2008 support with SeamlessRDP because I haven't been able to make it work.

All I get is the standard rdesktop windows when I try to connect using seamlessRDP.

Thank You,
Y.

---

### Post by samo_nz on 2011-06-27
ykorman place the seamless files from [http://www.cendio.com/seamlessrdp/seamlessrdp.zip]("http://www.cendio.com/seamlessrdp/seamlessrdp.zip") in C:\seamlessrdp

from the run program on windows run remoteprograms.msc

click change on RD Session Host Server Settings

under the RD Session Host Server tab select "allow users to start both listed and unlisted programs on initial connection"

in ubuntu run:
```
rdesktop -u <user> -d <domain> -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad" <server>
```

hope that helps anyone :)

---

