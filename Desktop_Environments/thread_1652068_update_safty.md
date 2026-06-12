---
title: "update safty"
date: 2010-12-24
forum: Desktop Environments
---

### Post by b1235762 on 2010-12-24
Today when I wanted to update my Ubuntu 10.04, after entering root password, it says something about :this can harm your system do u want to continue:
How can I check is the update is safe? In source I check all boxes without lucid-backports

[also Im unsure about that mark]("http://img9.imageshack.us/img9/1454/42698483.png")

---

### Post by Frogs Hair on 2010-12-24
I can't answer your question , but the links explain proposed updates and backports .   

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

---

### Post by b1235762 on 2010-12-27
anybody?

---

### Post by mcduck on 2010-12-27
You'll have to tell the exact error/warning you get, otherwise nobody will be able to help you with it and tell you what it means. :)

(Anyway, most likely reason for such warning is that you have added some additional software source, but didn't add the signing keys for that source. So downloaded files can't be checked for authenticity. That is usually harmless, but you should still add the missing signing key.)

What comes to the highlighted text on the picture yo attached, that's something that's *fixed* by the update, not something the update would cause. :D

Also, you probably don't want to enable the "proposed" repository. It's intended for testing new updates, after a while in "proposed" repository all the updates are moved to normal repositories. So unless you wish to actively test new updates before they are implemented you should leave it disabled. Backports is safe, though. It's just new package versions, backported from the current development release.

---

### Post by b1235762 on 2010-12-27
thx.

---

