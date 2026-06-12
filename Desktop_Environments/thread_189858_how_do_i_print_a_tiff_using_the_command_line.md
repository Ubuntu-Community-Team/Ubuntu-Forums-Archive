---
title: "how do i print a tiff using the command line"
date: 2006-06-05
forum: Desktop Environments
---

### Post by pubwho on 2006-06-05
I have a TIFF file and I want to print it to my USB printer. The printer is set up fine and works.

I don't want to use a GUI program, I just need to be able to send the TIFF to the printer using the command line. How do I do this?

---

### Post by pubwho on 2006-06-05
Ok, i think I've figured out how to do this myself:

```
lp fileName
```

If there is a better way, please let me know.

---

### Post by Pausanias on 2006-06-05
If that doesn't work, you could try this:

```

sudo apt-get install imagemagick
convert filename.tiff filename.ps
lp filename.ps

```

---

