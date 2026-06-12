---
title: "Do you find the close DVD tray button awkward?"
date: 2008-03-05
forum: Dell  Ubuntu Support
---

### Post by unutbu on 2008-03-05
Do you find the button to close the DVD tray awkward on the 530N?
I feel like I can barely get my fingernail on the button when the tray is sticking out. My work-around has been to close the tray from the command line with "eject -t" (see script below).

Does any else have this problem or have an easy way to close the tray physically?

```

#!/usr/bin/perl
system("eject");
print "close tray (press Return)";
<STDIN>;
system("eject -t");

```

---

### Post by gbrainin on 2008-03-05
I agree, the button is a bit hard to get at with the door in the way.  Thanks for the way cool workaround!

---

### Post by tjswain on 2008-03-31
I dont have the issue with the button, but this will work great for closing my DVD tray on my Home Theatre PC. Save me from having to get my lazy butt up off the couch.

One question: Is there some way for me to create an icon on my desktop to run this script?

---

