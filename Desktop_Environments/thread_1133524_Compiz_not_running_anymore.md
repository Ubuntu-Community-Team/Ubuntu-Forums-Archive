---
title: "Compiz not running anymore"
date: 2009-04-23
forum: Desktop Environments
---

### Post by afbase on 2009-04-23
I found out this afternoon that Compiz was no longer running on my computer.  from Compiz-check:
```

clinton@clinton-laptop:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility X1400
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

from glxinfo

```

clinton@clinton-laptop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

I've never had a problem with compiz until now.  I have no reason why this is the case either.  As compiz-check stated I'm still on intrepid ibex.   I changed my screen resolution about 2 weeks ago, but everything seemed fine when I did that.  I really have no idea why this issue is arising now.

---

### Post by afbase on 2009-04-23
okay nevermind.  I kept looking through the forum's other posts on compiz related issues.   I found that some had reinstalled their graphics driver.  I found that my ATI hardware driver was somehow not in use. I just reinstalled it and bingo! Compiz works like a charm again. :popcorn:

---

