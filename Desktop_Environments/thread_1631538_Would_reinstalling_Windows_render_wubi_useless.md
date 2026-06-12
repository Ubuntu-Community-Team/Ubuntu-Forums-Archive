---
title: "Would reinstalling Windows render wubi useless?"
date: 2010-11-26
forum: Desktop Environments
---

### Post by fred2028 on 2010-11-26
If I install Ubuntu 10.10 x64 from within Windows 7 x64 as dual boot (wubi) and then I reinstall Windows (clean install) on the Windows partition, would Ubuntu still function or does Ubuntu depend on Windows not to be reinstalled?

---

### Post by mikewhatever on 2010-11-26
Are you going to format the Windows partition? If yes, then all Ubuntu and wubi files will get deleted.

---

### Post by drs305 on 2010-11-26
To Windows, wubi is merely a file within Windows. So yes, a clean install of Windows would wipe it off the installation.

You could save the wubi file, /ubuntu/disks/root.disk and might be able to replace a fresh wubi install with the old root.disk after you have reinstalled Windows.

---

