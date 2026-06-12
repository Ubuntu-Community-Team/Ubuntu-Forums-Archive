---
title: "[SOLVED] FlightGear problem... looking weird"
date: 2008-05-20
forum: Gaming &amp; Leisure
---

### Post by Grone1985 on 2008-05-20
So I installed FlightGear and after loading the window looked like this... The output...
```
maitreyi@maitreyi-laptop:~$ fgfs
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.18 2007-01-15 12:50:45 ehofman Exp $
  Description:   Cessna C-172
Initializing Nasal Electrical System
power up

```

Any help?

Thanks!


FOUND THIS SOLUTION...

```
Corrupt Textures on ATi Cards

Several users have reported corrupted textures running FlightGear on ATi graphics cards. The ATi drivers are the subject of intensive improvement, but can still be problematic for some users. Try this:

Start FG in the normal way. Select 'View' drop-down menu (one from the left- you may not be able to read the labels!) Select 'Rendering Options' (fourth choice) Uncheck 'Use Point Sprites for Runway Lights' (fourth check-box)

When you come to quit FG, do so by menu: File...Exit, rather than closing the window to save this setting.
```

---

