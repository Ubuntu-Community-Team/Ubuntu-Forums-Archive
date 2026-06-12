---
title: "Problems installing/running GCC"
date: 2006-03-09
forum: Desktop Environments
---

### Post by Munkii on 2006-03-09
Hello

I installed Ubuntu the other day so I could use it as a development work station.

Shortly after installing, I tried running gcc from the terminal but the command wasnt recognized.
I checked the packages, and it said that "gcc-4.0.0" was installed.  I reinstalled it just to be sure, but that didnt change anything.

There are a few other packages with 'gcc' in the name, so I installed the packages "gcc" and "gcc-3.0.0".
After doing this, I could run the command 'gcc' from the terminal, but when I tried to compile an application, it failed because it can't find the libraries etc.

Can anyone please help me with this?
Do I need to install other packages, or can someone tell me how and what to add to my path?

Thanks in advance
Munkii :confused:

---

### Post by linear on 2006-03-09
Install the "build-essential" package. That should take care of it.

---

### Post by Munkii on 2006-03-10
It now works perfectly
Thanks so much :)

---

