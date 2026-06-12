---
title: "Can't load Matlab from Start Menu"
date: 2010-06-26
forum: Desktop Environments
---

### Post by buster2209 on 2010-06-26
I have installed Matlab into /opt/matlab and the file to run the program is located in /opt/matlab/bin and is called matlab.

I created a file;

> #! /bin/bash

/opt/matlab/bin/matlab

and placed it in /usr/bin.

From there, I can run matlab by typing 'matlab' in a Terminal window.

My problem is that I created a link in my start menu with the command 'matlab' but all I get is the splash screen for 5-10 secs then the program crashes out.  However, when I run it from a Terminal, it loads up just fine.

Any ideas as to why?

---

### Post by buster2209 on 2010-06-30
Figured it out;

> #! /bin/bash

/opt/matlab/bin/matlab [COLOR="Red"]-desktop[/COLOR]

---

### Post by cecilx22 on 2011-05-16
Thank you for this! Would have taken me hours to figure it out.

---

