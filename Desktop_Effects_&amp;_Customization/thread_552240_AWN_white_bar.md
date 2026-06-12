---
title: "AWN white bar?"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by czepluch on 2007-09-16
Hi. 

I've got this problem that I get a white bar where my AWN should be. I'm running compiz-fusion with emerald, so what could be wrong?

---

### Post by hyperair on 2007-09-16
It's probably a problem with the Compositing. If you're using nVidia, make sure your Screen section has this line:
```

Option "AddARGBGLXVisuals" "true"

```

---

