---
title: "Automatically close program upon hibernation"
date: 2009-04-22
forum: General Help
---

### Post by Spaceboy on 2009-04-22
Just wondered if anyone knew a way I could automatically shutdown/suspend a running application upon hibernation and possible restart the application when resuming from hibernation.  Thanks.

---

### Post by DagMan on 2009-04-23
the scripts in /usr/lib/pm-utils/sleep.d run in order of number during hibernate and suspend.  They run from lower number to higher number on suspend and higher to lower on resume.  Thing on suspend need to go under the part that says hibernate|suspend) and the things that run on resume need to go under thaw|resume)
killing applications shouldn't be a problem.
All these scripts run as root, which is a problem, so you'de need to put a little thought into it, for example to get a list of what things are actually running amoung those things that you would want brought back up, then figure out the proper work arounds for launching them as the proper user.

---

### Post by Spaceboy on 2009-04-26
Ok, thanks.  I created a script in that directory, which kills the application in question on hibernation.  However on resume the application isn't restarted.  Any idea what's wrong with my script below?  thanks.

#!/bin/sh

case "$1" in
	hibernate|suspend)
killall deluge
;;
	thaw|resume)
sleep 10
deluge
;;
esac

---

