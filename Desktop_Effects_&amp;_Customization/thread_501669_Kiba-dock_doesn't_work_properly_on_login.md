---
title: "Kiba-dock doesn't work properly on login"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by Ultra Magnus on 2007-07-15
I'm having an odd problem with kiba-dock, it works fine, except when I enable it to start when I log in by adding a new session /usr/bin/kiba-dock

it loads but when I open new windows, they don't show up on the dock.

Bit wierd, anyone know how to fix it?

---

### Post by Merlins on 2007-07-16
I noticed the same thing.  In my non-techi thinking I guessed it might be something to do with kiba-dock starting up before it can register a handle to the desktop.  To solve, I created a little startup script which did a pause for 5 or so seconds and then started kiba-dock.  I run the script during session startup instead of kiba-dock directly.  This way the desktop starts up, and after a short delay, kiba-dock appears - this works every time for me.  If you want exact details, let me know and I can post when I get home tonight.
------
Here is the script:

#!/bin/bash
sleep 12
kiba-dock

I put this in a file called startkiba.sh, which was what I called during startup (needs to be executable).

---

