---
title: "Getting errors installing Steam"
date: 2006-10-13
forum: Gaming &amp; Leisure
---

### Post by boast on 2006-10-13
Wine 0.9.22

Steam starts, I click next, next, and then it closes, with this in the terminal.
```
user@UbuntuBox:~/Desktop$ wine SteamInstall.exe
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF4ff3.tmp") : returns fake  SECURITY_DESCRIPTOR
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF503f.tmp") : returns fake  SECURITY_DESCRIPTOR
wine: Call from 0x7ed8212a to unimplemented function riched20.dll.RichEdit10ANSI WndProc, aborting
wine: Unimplemented function riched20.dll.RichEdit10ANSIWndProc called at addres s 0x7ed8212a (thread 0013), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
00000012 (D) (null)
        00000013    0
00000008
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0

```

any idears?

---

### Post by ciscosurfer on 2006-10-13
Are you trying to [install this]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=steam&searchon=names&subword=1&version=dapper&release=all")?  (why are you using Wine?)  Perhaps I'm confused...you can install Steam via apt.  To install you need your universe repository enabled.

---

### Post by boast on 2006-10-14
> **ciscosurfer said:**
> Are you trying to [install this]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=steam&searchon=names&subword=1&version=dapper&release=all")?  (why are you using Wine?)  Perhaps I'm confused...you can install Steam via apt.  To install you need your universe repository enabled.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)

---

### Post by Doctoxic on 2006-10-14
would it make any difference to the games you run from steam whether you install and run through wine or apt?

only i installed steam through wine - but HL2 won't run

Doc

---

### Post by crazedgremlin on 2006-10-14
apt installs a program called sTeam.  Not Steam.  I don't know what sTeam does, but I'm sure it's not Steam.

---

### Post by boast on 2006-10-14
bah, I had riched20.dll in override library.

Man, wine is horrible with steam, glitches everywhere. I guess i'll use cxoffice till demo runs out.

---

