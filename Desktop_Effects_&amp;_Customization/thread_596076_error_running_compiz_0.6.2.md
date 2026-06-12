---
title: "error running compiz 0.6.2"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by biasquez on 2007-10-29
hi, i compiled last version of compiz/compiz fusion with all lib and plugins. 
running  compiz --replace,  i have this error:

compiz (core) - Warn: Unable to parse XML metadata from file “core.xml”
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0


N.B. i use open-source driver radeon for my radeon mobility 9700 that run well on old compiz (default gutsy)

help plz!!!

---

### Post by Supersaiyan.IV on 2007-10-29
> **biasquez said:**
> hi, i compiled last version of compiz/compiz fusion with all lib and plugins. 
running  compiz --replace,  i have this error:

compiz (core) - Warn: Unable to parse XML metadata from file “core.xml”
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0


N.B. i use open-source driver radeon for my radeon mobility 9700 that run well on old compiz (default gutsy)

help plz!!!

Try this:

```

LIBGL_ALWAYS_INDIRECT=true compiz --replace --sm-disable --indirect-rendering ccp &

```

just copypaste in shell

---

### Post by biasquez on 2007-11-01
i compiled using git rep, now works well.

---

