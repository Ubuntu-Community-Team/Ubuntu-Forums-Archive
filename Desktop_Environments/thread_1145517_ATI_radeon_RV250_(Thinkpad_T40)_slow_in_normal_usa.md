---
title: "ATI radeon RV250 (Thinkpad T40) slow in normal usage"
date: 2009-05-01
forum: Desktop Environments
---

### Post by mcarro on 2009-05-01
Hello.  An old, but still working great, Thinkpad T40 has installed an ATI Radeon RV250.  It is too old for the native driver, I understand, but I am *not* using compiz or fancy 3D graphics.  However, Ubuntu 8.10 was working great with, e.g., going through a PDF file with evince, and now this has slowed down noticeably: "turning" a normal page (no graphics) becomes a matter of seconds, with a pause in the middle where the display does not reflect neither the first nor the second page.

Something similar happens when switching desktop: empty windows appear which take some time to fill in.

Has anybody experienced this?  Any idea of how can I improve on this situation?

---

### Post by asbesto on 2009-05-02
Same problem here. It seem a race condition for me: cpu at 50%, firefox at 35%. Compiz now is slow as hell! I will reinstall 8.10 soon...

...now.

:confused:

---

### Post by krazyd on 2009-05-02
Try adding this line to the Device section of your xorg.conf (or edit the line if a current accelmethod line is in place). Some of the older radeons have buggy exa implementation. Exa acceleration is the default now for jaunty while xaa was default in intrepid.

```
Option    "AccelMethod" "xaa"
```

---

### Post by asbesto on 2009-05-02
I think my solution is good for you:

[URL="http://ubuntuforums.org/showthread.php?t=1146068"]http://ubuntuforums.org/showthread.php?t=1146068
[/URL]

It solved this problem on my ATI Radeon Mobility 7500.

---

### Post by mcarro on 2009-05-05
> **asbesto said:**
> I think my solution is good for you:

[URL="http://ubuntuforums.org/showthread.php?t=1146068"]http://ubuntuforums.org/showthread.php?t=1146068
[/URL]

It solved this problem on my ATI Radeon Mobility 7500.

I have adopted it and it worked like a charm. I can also turn on some compiz effects with no negative effects in performance (with 8.10 even turning on compiz with no effects made the machine sluggish -- e.g., scrolling in firefox was a pain).

EDITED: it should be made default for at least some (old?) videocards / chips in 8.10.  It is otherwise a step back in usability.

Thanks a lot!

---

### Post by orawax on 2009-09-30
Also check this, works perfectly for me:
[http://ubuntuforums.org/showpost.php?p=7804812&postcount=2](http://ubuntuforums.org/showpost.php?p=7804812&postcount=2)

(See also postcount=3...)

---

