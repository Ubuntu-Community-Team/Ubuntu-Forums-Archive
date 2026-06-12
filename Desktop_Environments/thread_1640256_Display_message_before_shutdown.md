---
title: "Display message before shutdown"
date: 2010-12-07
forum: Desktop Environments
---

### Post by applerock79 on 2010-12-07
I have been working on this for all afternoon.
I have found links here and elsewhere, with no solution.

(currently) I am using crontab to execute the shutdown command based on a schedule. M-W, Th-Fr, and Sat.
The message argument does not work. I need a Gui warning message before the Pc kicks the user off.

Zenity does not work directly with crontab, so I put it in a script:

#!/bin/bash
zenity --warning --text "The library is closing in 10 minutes. This PC will automatically shutdown in 5 minutes. Please save your work now, to prevent data loss."

no work. Tried adding 00 06 * * * env DISPLAY=:0 zenity
No dice.

Put zenity into the script.
Tried (in my crontab)
00 06 * * * env DISPLAY=:0 /home/mydir/myscript.sh
No dice.


This should not be this hard.
All I want to do is display a message based on a schedule.
Then shut down the PC 5 min after that.
And do this all automatically, without having to run a program each time the Pc boots up.
I've read that zanity is not compatible with crontab.
Then it's useless for this.

Tried Gscheduler. Could not make up a schedule like I needed.

I don't need to use crontab or zanity. I could care less, as long as I can get a darn msg displayed before shutdown. Seemed that fit the bill if I could only get it to display a gui msg.

frustration is settling in (could you tell?)

---

### Post by applerock79 on 2010-12-08
Well, I deleted most of the crontab file, and just put in my commands. Then, after a reboot, it works.
(I deleted all the comment out)

Not sure what fixed it. Deleting the comments (doubt that) or rebooting, yet another time. (doubt that too, since I had rebooted several times during this process.)

So.....I don't know what really fixed it. But it now works.

---

