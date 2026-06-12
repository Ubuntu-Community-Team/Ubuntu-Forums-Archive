---
title: "Can I turn off tracker?"
date: 2009-05-10
forum: General Help
---

### Post by jerlinux on 2009-05-10
After the ubuntu upgrade, tracker has a problem with my drive.  It thinks the index is corrupted.  That's nice.  But it will not go away.  Is there any way to tell tracker that I don't want it to run?

Thanks

---

### Post by lovinglinux on 2009-05-10
Go to "System >> Preferences >> Session" or "System >> Preferences >> Startup Applications" if you are using Jaunty.  Untick all tracker related stuff.

---

### Post by Indian Summer on 2009-05-10
I think it's better to just fix it. I just had this problem myself, but fixed it by installing tracker-utils, then running "tracker-processes -r" and logging out.

There was another thread on here about it that describes it better:
[http://ubuntuforums.org/showthread.php?t=1135629](http://ubuntuforums.org/showthread.php?t=1135629)

---

### Post by jerlinux on 2009-05-12
For the time being, I have turned off tracker.  When things calm down around here, I will try to "fix" it correctly.

Thanks to everybody who responded.

---

