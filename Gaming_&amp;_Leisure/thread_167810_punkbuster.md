---
title: "punkbuster"
date: 2006-04-29
forum: Gaming &amp; Leisure
---

### Post by Smokemare on 2006-04-29
okay told to run the game sudo quake3 to get pb to update
jhow do i run xqf with root permissions or can i set up a user with root permissions?

---

### Post by minisori on 2006-04-29
When you have to run the game with sudo to get updates is because your .quake3 folder in your home has root as owner, do sudo chown -R smokemare:smokemare .quake3, so you can run it as normal user.

It's the same as here:

[http://ubuntuforums.org/showthread.php?t=167057](http://ubuntuforums.org/showthread.php?t=167057)

---

