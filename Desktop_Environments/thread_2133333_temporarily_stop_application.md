---
title: "temporarily stop application?"
date: 2013-04-07
forum: Desktop Environments
---

### Post by chitowner2 on 2013-04-07
Hello All,

I don't find this on my cheat list...

I want to know how to temporarily stop/freeze/interrupt/halt an application for which I know the PID, using a terminal command -    BUT NOT    kill/terminate it.
Then of course I need a command to resume.  

I googled around some, but either I am not using the right terms to search or I just can't find a solution out there. I'm pretty sure this is dirt-simple for somebody.

Thanks!
CT

---

### Post by papibe on 2013-04-07
Hi chitowner2.

You can use the signals STOP and CONT from the kill command. For example:
```
kill -STOP pid

kill -CONT pid
```
Regards.

---

### Post by stinkeye on 2013-04-07
I have a script you could probably adapt to toggle pause/resume your application.

I found that running **ps aux** and grepping my countdown script gave different values when running and paused.
When countdown.sh is running...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **ps aux | grep -m 1 "countdown.sh"** 
glen     12796  0.1  0.0  16568  1480 ?        [COLOR="#FF0000"]S[/COLOR]    08:36   0:00 /bin/bash /home/glen/conky/conky-indicators/countdown.sh 00:03:00
```

When countdown.sh is paused....
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **ps aux | grep -m 1 "countdown.sh"** 
glen     12796  0.0  0.0  16568  1480 ?        [COLOR="#FF0000"]T[/COLOR]    08:36   0:00 /bin/bash /home/glen/conky/conky-indicators/countdown.sh 00:03:00

```

So I made a script that will pause countdown.sh if running and resume if paused.
```
#!/bin/bash
#Script to pause Conkytimer
# click to stop, click to continue

STATUS=$(ps aux | grep -m 1 "countdown.sh"  | awk '{print $8}')

if [ "$STATUS" == "[COLOR="#FF0000"]S[/COLOR]" ]
then
	exec killall -s STOP countdown.sh &
	notify-send -i /home/glen/conky/conky-indicators/Bell.png -u critical "Timer Paused"	 
else
  exec killall -s CONT countdown.sh &
  notify-send -i /home/glen/conky/conky-indicators/Bell.png -u critical "Timer Continued"

fi
exit 0
```

This script enables me to add a pause/resume item to my timer's quicklist menu.

---

### Post by chitowner2 on 2013-04-07
Yup! 
That's it! 
I found the man page. I am now more educated!


> **papibe said:**
> Hi chitowner2.

You can use the signals STOP and CONT from the kill command. For example:
```
kill -STOP pid

kill -CONT pid
```
Regards.

---

