---
title: "Shell permissions"
date: 2009-04-19
forum: General Help
---

### Post by brigadoon on 2009-04-19
I have recently loaded in Ubuntu 8.10 on a Sony Vaio laptop. It is a dual boot with Vista. Loading in programs through the package manager works OK. However, I am having trouble getting scripts and shells to work properly. I can get a .csh to run but when a new file is generated the shell locks up. This happens with dash and bash. The scripts will freeze up. I keep getting error messages stating that the file or folder cannot be written to. I didn't have this issue with previous versions of Ubuntu. Has anyone else come across this. If so what is a good work around.

---

### Post by ibuclaw on 2009-04-19
What sort of scripts are you running?

Could you post a simple script that fails to run?

Regards
Iain

---

### Post by paradigm2 on 2009-04-19
> **brigadoon said:**
> I have recently loaded in Ubuntu 8.10 on a Sony Vaio laptop. It is a dual boot with Vista. Loading in programs through the package manager works OK. However, I am having trouble getting scripts and shells to work properly. I can get a .csh to run but when a new file is generated the shell locks up. This happens with dash and bash. The scripts will freeze up. I keep getting error messages stating that the file or folder cannot be written to. I didn't have this issue with previous versions of Ubuntu. Has anyone else come across this. If so what is a good work around.

What are the errors saying when they tell you that it cannot write?  Permission denied?  If so you need to check the permissions.

See [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for basic info.

---

### Post by brigadoon on 2009-04-25
Thanks for the interest and offers of help. Updating to Ubuntu 9.04 solved the problem. On balance 9.04 appears to be a much better build.

---

