---
title: "Steam for Linux won't start"
date: 2013-02-07
forum: Gaming &amp; Leisure
---

### Post by ohwhynow on 2013-02-07
Hello, 

I recently installed latest version of Steam .deb package from their site. Everything went smoothly up until I decided to actually START steam. It doesn't matter if I start it from dash or from Terminal, all I get is this error:

> Error: Couldn't find Steam install license agreement, aborting!


Did anyone of you, fellow Ubuntu users, run into that kind of error? Or maybe someone may have an idea what's wrong?

I'm sorry for any grammatic or spelling mistakes, english isn't my native language.

---

### Post by drawkcab on 2013-02-07
> **ohwhynow said:**
> Hello, 

I recently installed latest version of Steam .deb package from their site. Everything went smoothly up until I decided to actually START steam. It doesn't matter if I start it from dash or from Terminal, all I get is this error:



Did anyone of you, fellow Ubuntu users, run into that kind of error? Or maybe someone may have an idea what's wrong?

I'm sorry for any grammatic or spelling mistakes, english isn't my native language.

Your English is great!

I didn't have any problems installing steam.  Are you installing in on 12.04 or 12.10?  Have you tried purging it and reinstalling it?

---

### Post by georgesperosjr on 2013-02-07
I have the same problem.


> **ohwhynow said:**
> Hello, 

I recently installed latest version of Steam .deb package from their site. Everything went smoothly up until I decided to actually START steam. It doesn't matter if I start it from dash or from Terminal, all I get is this error:

Error: Couldn't find Steam install license agreement, aborting!

Did anyone of you, fellow Ubuntu users, run into that kind of error? Or maybe someone may have an idea what's wrong?

I'm sorry for any grammatic or spelling mistakes, english isn't my native language.

---

### Post by georgesperosjr on 2013-02-07
The answer is found on this thread at Github:

[https://github.com/ValveSoftware/steam-for-linux/issues/1386](https://github.com/ValveSoftware/steam-for-linux/issues/1386)


> **georgesperosjr said:**
> I have the same problem.

---

### Post by ohwhynow on 2013-02-08
It was 12.10 64-bit, I forgot to mention that. Anyway, georgesperosjr's answer is correct. Seems to be problem with recent installers and 64-bit 12.10, unless someone else will report with the same error from Precise. In case anyone wants to know what they are accepting while doing that, here is THE license agreement in attachment: by the way, it was actually directory higher, so I believe it should be:

```
cp ~/.steam/steam_install_agreement.txt ~/.steam/steam/steam_install_agreement.txt
```

EDIT:
Oh, and in case anyone has the same problem with Steam whining about 32-bit libgl.so.1: it actually exists, what you need to do is to create link /usr/lib/i386-linux-gnu/libgl.so.1 to /usr/lib/i386-linux-gnu/mesa/libgl.so.1. You will need root access and it doesn't matter if it is done using terminal or file manager(e.g. nautilus).

Quantal Quetzal 64-bit and Steam surely don't seem to get along very well. It's a shame, because 12.10 seems to work perfectly to me, and abosolutely everything works (including Nvidia Optimus and hibernation) with exception of Steam until now.

---

