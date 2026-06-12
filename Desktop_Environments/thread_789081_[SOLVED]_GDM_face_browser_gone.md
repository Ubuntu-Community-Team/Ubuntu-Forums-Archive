---
title: "[SOLVED] GDM face browser gone"
date: 2008-05-10
forum: Desktop Environments
---

### Post by marriedman on 2008-05-10
I have been having weird happenings with GDM ever since the upgrade to Hardy, but today I woke up and came to log on and my face browser is missing. It's like I have no users set up on the computer.

I can manually type my name and password in no problem, but no matter what theme I choose there is never a face browser or user list shown. Anyone have ANY ideas?

Paul

---

### Post by Zorael on 2008-05-10
Isn't there an option to toggle 'user list' in the login manager settings in Gnome? Perhaps memory fails me.

In KDE, the user list is a completely different theme, so you'd have to manually edit some files to enable/disable it.

---

### Post by marriedman on 2008-05-10
I don't see anything about toggling the user list, I only see where one can change GDM themes. I checked to see if somehow my users got hidden from the list, but they are there too.

---

### Post by BigBob on 2008-05-10
Hi all,

Exactly same as marriedman on my side, the userlist selector seem to be gone ...

A++

---

### Post by BigBob on 2008-05-10
Ok,

After searching on google, here is the fix :

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931)

A++

---

### Post by marriedman on 2008-05-10
Confirmed. That fixed my problem. Strange, I swear that link was not there when I looked this morning. Thanks man. I appreciate that!

---

