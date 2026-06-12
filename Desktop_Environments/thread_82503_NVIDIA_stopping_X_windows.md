---
title: "NVIDIA stopping X windows"
date: 2005-10-26
forum: Desktop Environments
---

### Post by sicness on 2005-10-26
Hey guys,

I need to install the latest nvidia drivers and I need to stop X windows before I install it, how do I do that?  Thanks.

---

### Post by ippiraman on 2005-10-26
Do you really need to stop X Windows? You can actually install the nvidia drivers while running X. But you'll have to restart X for the drivers to take effect. So here goes...

Ctrl+Alt+Backspace

HTH

---

### Post by Xian on 2005-10-26
I assume you have a reason for doing this manually since
the nvidia packages are in the 5.10 repository.

From the desktop:

Ctrl+Alt+F1

Login as user at the command prompt
Issue this command to stop X:

$ sudo /etc/init.d/gdm stop

Apply the nVidia driver as instructed.
Issue this command to start X:

$ sudo /etc/init.d/gdm start

---

### Post by Mustard on 2005-10-26
Might I suggest you read this too?

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

---

