---
title: "Just installed Audacity...error message on startup (won't play / record audio)"
date: 2006-04-03
forum: Desktop Environments
---

### Post by bpont on 2006-04-03
Here's the output of the error message:

[COLOR="Red"]There was an error initializing the audio i/o layer.
You will not be able to play or record audio.

Error: Host error.[/COLOR]

Then when I go to "file/preferences" there's no entry on the playback device section.

Any suggestions?

---

### Post by tehwa on 2006-04-03
Make sure that no other audio applications are running. Audacity wants exclusive control of your audio card but other apps aren't letting it.

If you think you have all audio apps closed and it still errors, log out/log in to a fresh session and open Audacity. If it still fails, you may need to adjust some config.

---

### Post by beefsprocket on 2006-04-03
I always just kill artsd and esd when starting audacity. A simple script does the trick very well:

#!/bin/bash
killall artsd
killall esd
audacity &

---

### Post by bpont on 2006-04-03
[QUOTE=beefsprocket]I always just kill artsd and esd when starting audacity. A simple script does the trick very well:

#!/bin/bash
killall artsd
killall esd
audacity &[/QUOTE]

beefsprocket: indeed, killall esd did solve the problem...do i even need esd?  and why is audacity so persnickety about total control?

anyway, problem solved, so thank you  :D

---

