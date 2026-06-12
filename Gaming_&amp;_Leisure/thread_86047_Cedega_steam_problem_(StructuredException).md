---
title: "Cedega steam problem (StructuredException)"
date: 2005-11-04
forum: Gaming &amp; Leisure
---

### Post by spudse on 2005-11-04
Hello, I switched to Ubuntu/linux about two weeks ago. I decided not to install Steam/Counter-strike 1.6 right away. Now after two weeks of struggle, I decided I really need cs ;)

I installed Cedega (4.4.1), installed steam and after that it started updating (steamlike:) ). After updating, steam seems to be gone and after some time I receive this message:
```

ERROR
Steam.exe (main exception): Win32
StructuredException at 58E43CFF : Attempt to read 
from virtal adress 7275042 without appropriate 
access rights.
[OK]
```
I found on some forum that it was caused by a .blob file which should be deleted. So I went to the ~/.transgaming/c_drive/Program Files/Steam dir and manually deleted the file. But then Steam errors about a blob file that couldnt be opened.

Does anybody know a solution to this problem? I really need to play my fav game of all times again :)

---

### Post by frodon on 2005-11-04
First i have to say that i got some problems with cedega 4.4.1 and the latest change in the steam interface so i had to install cedega 4.4.3 to solve these problems, so i advice you to install cedega 4.4.3 it could solve your problem.
I never needed to tweak anything to get cedega and steam working so i think your problem is more due to the latest steam interface changes (since 1 week).

---

### Post by spudse on 2005-11-04
Thanks Frodon.

However, I installed Cedega 4.4.3-1, with cedega I try to install SteamInstall.exe.

Everything goes fine, Steam asks if I want to use an existing account or create a new account, I chose existing. I type in my email/password and then it says "connection Steam account: *email@address.com*" (all normal) and then I get the error:

```
Fatal Error: Failed to load platform modules
```

Anyone has an idea what this might be?

---

### Post by spudse on 2005-11-04
I seem to have mixed up old installs of steam and root/user. I installed steam to a new directory and everything seems to go fine. I'm installing cs16 right now :)

---

