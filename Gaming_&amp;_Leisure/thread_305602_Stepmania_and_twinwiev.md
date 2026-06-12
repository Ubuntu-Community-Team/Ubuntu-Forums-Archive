---
title: "Stepmania and twinwiev"
date: 2006-11-23
forum: Gaming &amp; Leisure
---

### Post by Lusse on 2006-11-23
After I chanced to twinwiev stepmania wont display correct. It is in the down right corner and not the whole is shown. Really need help!!! Please  ](*,)

---

### Post by hikaricore on 2006-11-23
I'm guessing that twinview is a multimonitor setup?  I don't think that stepmania supports this, you'll probably have to have it set in windowed mode to run properly.

If the game will not start edit your Stepmania.ini file.

For example, mine is located at:
/media/devistate/linux.bin/stepmania/Data/StepMania.ini

your location will differ but it will always (almost) be in the Data directory of the stepmania or Stepmania folder.

Find the line that says:

```
Windowed=0
```

Which is usually at the bottom and change the 0 to a 1.

Hope this helps.

--Aaron

---

