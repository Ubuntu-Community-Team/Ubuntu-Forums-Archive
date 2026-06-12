---
title: "Access Windows Desktop from PCManFM (Wubi Lubuntu 12.04)"
date: 2012-07-27
forum: Desktop Environments
---

### Post by Lyfang on 2012-07-27
Hi, when I try to open the Windows Desktop with PCManFM I get: The specified directory does not exist. I've Wubi Lubuntu 12.04 installed on Windows 7. Why can't I access /host/Users/USERNAME/Desktop? Any help is greatly appreciated!

---

### Post by Frogs Hair on 2012-07-27
You can access files via host with Wubi but you can't open the Windows desktop. Windows is not running while Ubuntu is in use it only uses the Windows boot loader. If I remember right you can access the some of individual folders that make up the Windows desktop directory. These include User Name and Libraries but I'm not sure about Computer , Network and Home Group.

---

### Post by Lyfang on 2012-07-28
I can access /host/Users/USERNAME/Desktop from another computer with Wubi Lubuntu 12.04 installed.

---

### Post by Frogs Hair on 2012-07-28
> **Lyfang said:**
> I can access /host/Users/USERNAME/Desktop from another computer with Wubi Lubuntu 12.04 installed.

USERNAME is part of that directory or at least my user name folder appears under desktop in windows 7.

---

### Post by Lyfang on 2012-07-28
> **Frogs Hair said:**
> USERNAME is part of that directory
Yes. To clarify USERNAME: means ${USER_NAME} or even better clarification; the account name that was given at the Windows installation...

---

