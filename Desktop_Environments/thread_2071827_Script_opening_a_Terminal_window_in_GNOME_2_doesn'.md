---
title: "Script opening a Terminal window in GNOME 2 doesn't in MATE."
date: 2012-10-16
forum: Desktop Environments
---

### Post by james_mcl on 2012-10-16
I've installed MATE in Xubuntu Precise, and while it's a great GNOME 2-a-like, I have had a couple of minor issues with it - and I'm hoping someone here can help me with this one, as nobody on forums.mate-desktop.org was able to.

I've got a bash script which I've added to System - Preferences - Startup Applications to carry out various housekeeping tasks and print information to the screen on what it's doing. This is part of the code:

```

    echo "About to delete formhistory.sqlite."
    for y in `ls .mozilla/firefox/*.default/formhistory.sqlite`; do
       rm $y
    done

```

In Gnome 2, when I logged in, a terminal window would appear in which the various "echo" outputs would show. This window would eventually vanish when the script was finished.

In MATE, no such window appears. I've been checking on the deleted files and the script otherwise appears to be working, but since the script was supposed to use echo to output any error messages, it's impossible for me to tell for sure.

How can I get a terminal window to appear for echo's output? And can anyone tell me where it's currently being sent to?

Thanks,

James McLaughlin.

---

### Post by PowerBarry43 on 2012-10-16
try changing your script to this

```

#!/bin/bash
terminal

echo "About to delete formhistory.sqlite."[INDENT]for y in `ls .mozilla/firefox/*.default/formhistory.sqlite`; do[INDENT]rm $y
[/INDENT]done
[/INDENT]exit
```hope this helps!

Barry

---

### Post by james_mcl on 2012-10-16
A bit red-facedly, I was actually logging on to post another solution and then spotted yours above!

I removed

```

/home/(my username)/remove_flash_cookies_and_sqlites.sh

```

from Startup Applications, and then added

```

mate-terminal -e /home/(my username)/remove_flash_cookies_and_sqlites.sh

```

which achieved the desired effect.

---

