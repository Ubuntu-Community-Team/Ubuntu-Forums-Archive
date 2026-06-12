---
title: "Lock Screen During Certain Hours of The Day"
date: 2017-12-04
forum: Desktop Environments
---

### Post by emc5ud on 2017-12-04
Hello, I would like to set up an Ubuntu Machine to never lock the screen during work hours (M-F 8-6) and automatically stop displaying or go to screen saver during all other times. I have heard of cuttlefish, but apparently it is not supported in 16.04. Any suggestions?

---

### Post by linuxsecrets on 2017-12-06
You can create something like this with a script.

If you want me to make something I could if you want?

---

### Post by shintaomonk on 2017-12-07
Was about to suggest a script and found u beat me to it, though I don't know offhand what the command to lock lubuntu is.

---

### Post by again? on 2017-12-09
Lubuntu appears to use light-locker.
light-locker-command has a poke option.
> **-p, --poke**
              Poke the running locker to simulate user activity
You could use "light-locker-command --poke" in a loop script to inhibit screen locking.
eg
_screenlock-schedule.sh_
```
#!/bin/bash

while [ 1 ]; do 

	# get day of week
	day=$(date +%u)
	 
	# reset weekend indicator flag
	weekend=false
	 
	# if day of week is 6 or 7, then it's a weekend
	[ $day -ge 6 ] && weekend=true
	 


	if [ $weekend = "false" ]; then

			HOUR=$(date +%H)
			case "$HOUR" in

			# work hrs
			08|09|10|11|12|13|14|15|16|17)
			echo "Working hours. Screenlock is inactive"
			light-locker-command --poke
			;;

			# after hrs
			18|19|20|21|22|23|00|01|02|03|04|05|06|07)
			echo "After hours. Screenlock is active."
			;;
			esac

	else
			echo "The weekend. Screenlock is active."
	fi
	sleep 60
done
exit 0
```

Should inhibit the screen locker between the hours of 8am to 6pm on weekdays.
You can test by running the script in terminal and opening "time and date".
Unlock, change to "manual" and try different times.(may want to change "sleep 60" to "sleep 15" in the script, while testing)

---

