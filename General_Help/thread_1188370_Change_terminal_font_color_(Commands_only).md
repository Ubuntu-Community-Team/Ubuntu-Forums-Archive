---
title: "Change terminal font color (Commands only)"
date: 2009-06-15
forum: General Help
---

### Post by wbest on 2009-06-15
I need commands that can change the color of the font in terminal.
I'm writing a perl script and need to change the font color only, I have a sript that changes background, but not foreground.  So I was hoping to get some commands that can do it and put them in perl.

---

### Post by sdennie on 2009-06-15
Try:

```

sudo apt-get install libansicolor-perl

```

Then, in your code:

```

use Term::ANSIColor;

print color("blue"), "This is blue\n", color("reset"), "This is normal\n";

```

---

