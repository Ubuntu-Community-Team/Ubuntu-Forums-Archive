---
title: "Make the keyboard volume up button extend volume over 100 %?"
date: 2013-04-27
forum: Desktop Environments
---

### Post by hoopotus2 on 2013-04-27
Is there a way to make the keyboard volume up button set volume over 100 %?

When I go to "Sound Preferences", I can slide the volume bar to its maximum which is 150 %, but using the keyboard volume up button (or whatever button I bind to increase volume), it stops at 100 %.

It would be very convenient to make it go over 100 %, because keyboard is much more convenient than going to the sound preferences, and the circumstances at my desktop computer are such that I have to use my monitor's speakers, and those set at maximum, the volume is often still a little too low at 100 %.

---

### Post by stinkeye on 2013-04-27
This script works for me to increase the volume beyond 100%.

```
#!/bin/bash

pacmd dump | awk --non-decimal-data '$1~/set-sink-volume/{system ("pacmd "$1" "$2" "$3+[COLOR="#EE82EE"]2500[/COLOR])}'
```
Test the command in terminal with you sound settings open and if it works make a custom shortcut.
You can change the stepping by changing the [COLOR="#EE82EE"]2500[/COLOR] value.

In keyboard shortcuts,
add the path to the script as the command and use ctrl+"your volume key" as the shortcut.

---

### Post by hoopotus2 on 2013-04-29
This works. Thank you very much.

---

