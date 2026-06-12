---
title: "Discovering currently active user -- is there easier way"
date: 2010-01-06
forum: Desktop Environments
---

### Post by mteppo on 2010-01-06
I wanted to implement a simple logging utility on usage time.
There may be one already - if so please direct me to it.

The current solution - however - was cooked on top of dbus.

```
	
#Check if there is anyone at all with active session?
idle=`dbus-send --system \
          --dest=org.freedesktop.ConsoleKit \
          --type=method_call --print-reply  \
          --reply-timeout=20000 \
    	  /org/freedesktop/ConsoleKit/Manager \
          org.freedesktop.ConsoleKit.Manager.GetSystemIdleHint | grep -c "boolean true"`
	if [ $idle = 0 ] ; then

		curseat=`dbus-send --system \
		     	--dest=org.freedesktop.ConsoleKit \
		     	--type=method_call --print-reply \
		     	--reply-timeout=20000 \
	           	/org/freedesktop/ConsoleKit/Manager \
			org.freedesktop.ConsoleKit.Manager.GetSeats | grep path | cut -d '"' -f 2` 
		#echo $curseat
		cursession=`dbus-send --system \
		     	--dest=org.freedesktop.ConsoleKit \
		     	--type=method_call --print-reply \
		     	--reply-timeout=20000 \
	           	$curseat \
			org.freedesktop.ConsoleKit.Seat.GetActiveSession | grep path | cut -d '"' -f 2`
		#echo $cursession				
		curuid=`dbus-send --system \
		     	--dest=org.freedesktop.ConsoleKit \
		     	--type=method_call --print-reply \
		     	--reply-timeout=20000 \
	           	$cursession \
			org.freedesktop.ConsoleKit.Session.GetUnixUser | grep int32 | cut -d " " -f 5-`
		#echo $curuid
                #grep UID from etc/passwd -- there may well be utility for doing this proper...
		user=`grep x:$curuid /etc/passwd  | cut -d ":" -f 1`
		echo "`date`: System is active. User = $user"		

	fi


```

This seems quite awkward but sort of works.
I did implement a utility that calls this kind of script once a minute and logs the result.
The main point for me is that there are multiple users that leave session locked when they exit and next one just clicks "Switch User" button - so I just cannot simply get the gdm processes as most propaly all users have sessions (idleing).
Also I do not want to limit the users session times -- just log them -- as limiting would be possible with timeoutd.

So the main question -- I guess here -- is that is there a more easy or right way to do this? I'd hate to maintain something just to notice in few years that it wont be needed as it never was...

---

