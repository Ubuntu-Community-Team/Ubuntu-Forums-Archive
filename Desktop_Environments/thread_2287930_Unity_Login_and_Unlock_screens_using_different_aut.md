---
title: "Unity Login and Unlock screens using different authentication methods"
date: 2015-07-23
forum: Desktop Environments
---

### Post by stuartjk1606 on 2015-07-23
Mainly just a quick check to ensure I am not going mad or messed something up.

I have a 14.04 default desktop build and enabling google-authenticator in a number of key entry points, one of which is desktop access. It would appear that lightdm PAM config is used to initially log in to the desktop but then once a desktop is running and subsequently "locked", the unity PAM config takes over. Is this correct? Also, is there any way to unify the 2?

I would like to keep the build as simple as possible and satisfied with maintaining the 2 separately if required, but personally it does not make a lot of sense to split out desktop authentication this way.

---

