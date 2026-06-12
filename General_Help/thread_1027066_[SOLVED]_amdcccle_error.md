---
title: "[SOLVED] amdcccle error"
date: 2008-12-31
forum: General Help
---

### Post by sixfivetwo on 2008-12-31
```
paul@paul-desktop:~$ amdcccle
Parse error on line 37 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.
Parse error on line 37 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.
Segmentation fault
```

I'm running Intrepid, everything is updated to the best of my knowledge. I just installed the Catalyst Control Center. It wouldn't start up from the Applications menu. I tried starting it through Terminal and the above is my result. How do I fix this?

---

### Post by dcstar on 2009-01-01
> **sixfivetwo said:**
> ```
paul@paul-desktop:~$ amdcccle
Parse error on line 37 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.
Parse error on line 37 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.
Segmentation fault
```

I'm running Intrepid, everything is updated to the best of my knowledge. I just installed the Catalyst Control Center. It wouldn't start up from the Applications menu. I tried starting it through Terminal and the above is my result. How do I fix this?

Well, you should look at "line 37 of section Module in file /etc/X11/xorg.conf" and find out why your app doesn't like it.

---

### Post by sixfivetwo on 2009-01-01
Since I know nothing (I should have said such earlier), I did not want to start editing stuff willy nilly.

I removed the line, and it works fine now.

---

