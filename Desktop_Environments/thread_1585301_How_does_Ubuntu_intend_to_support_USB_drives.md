---
title: "How does Ubuntu intend to support USB drives?"
date: 2010-09-30
forum: Desktop Environments
---

### Post by aajax on 2010-09-30
I am having great difficulty finding any documentation that describes how Ubuntu handles USB drives.  I am using several versions of Ubuntu (Desktop & Server also Kubuntu) and would especially like to know what packages are involved in providing USB support.  This should include both how the default installation is intended to work as well as possible alternatives that require the user to install packages.

I'd be most grateful to anyone who could point me to the appropriate documentation.

Many thanks!

---

### Post by leef on 2010-09-30
I can't point you to any specific documentation but I do know that a majority if not all USB device support is provided by the kernel. If you're referring to automount then I think that's handled by userland programs such as HAL (hardware access layer) and programs that interface with HAL. If nothing else this reply served to "bump" this question, sorry I couldn't provide any further help.

Edit: On a side note I use a program called halevt to deal with automount, I had to compile it since the version in the repo doesn't work very well (old version without bug fixes)

---

### Post by aarons6 on 2010-10-01
no issues with me, i have a WD Elements 2tb usb drive that i use.

its there when i boot up. nothing special was required to install.

---

