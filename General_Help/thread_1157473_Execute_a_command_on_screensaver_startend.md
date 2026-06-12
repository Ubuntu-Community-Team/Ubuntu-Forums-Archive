---
title: "Execute a command on screensaver start/end"
date: 2009-05-12
forum: General Help
---

### Post by jjmatt on 2009-05-12
Hey all,

I'd like to figure out how to execute a command when my screensaver starts or when I haven't used my computer in [some period of time, perhaps 5 minutes]. 

Basically, I'm setting up [motion]("http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome") to monitor my room when I'm not around (my roommates have a ridiculous amount of parties, I lock my door, but you can never be too safe) and I'd like to not have motion running while I'm sitting at the computer typing away, but I don't want to forget to turn it on when I leave, so I figure one way to determine if I'm there is by keyboard/mouse usage; If I'm using neither there's a possibility I'm not in the room. And I can't think of any other way to monitor this than by when my screensaver pops up.

It'd also be nice to have it shut down when I've been using the computer for [some other period of time. say five minutes?]. I know I could do something like (though I'm sure there are more elegant ways of doing it)

```
sleep 300s killall motion
```

But, I'd obviously need something to execute the command.

Does anyone have any ideas?

---

### Post by jjmatt on 2009-05-17
Ok, in case anyone in the future may be looking for this same solution, I've got it working (though, truthfully, it's not the most elegant solution-I literally learned shell scripting just to get this to work, and programming isn't my forte...but like I said, it works) by checking out [this page]("http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#head-ac43c8f33bc700a5e298e6a82ded0e8bb9b33043") which I think has it written in c shell and rewriting it for bash. Anyway, on to the code:

```
#!/bin/bash

# Make sure that all of the container files are empty before starting
rm /home/[location]/[of]/motionfile*
touch /home/[location]/[of]/motionfile1 /home/[location]/[of]/motionfile2 /home/[location]/[of]/motionfile3 /home/[location]/[of]/motionfile4 /home/[location]/[of]/motionfile5

# Output data that dermines if the screensaver is turning on or off (or neither)
dbus-monitor --session type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'  >> /home/[location]/[of]/motionfile1 &

# Make this happen indefinitely. There's probably a much better (read: safer)  way of doing this.
while [ 1 > 0 ] ; do

	#Count the number of lines in motionfile1
	S5=$(wc -l /home/[location]/[of]/motionfile1 | awk '{print $1}')

	#If there are not exactly 2 lines then remove the garbage information from the front of motionfile1 and put the rest in motionfile2
	#If there are exactly 2 lines, then just overwrite motionfile2 with motionfile1
	if [ $S5 -ne 2 ] ; then
		sed '1,/^signal/d' </home/[location]/[of]/motionfile1> /home/[location]/[of]/motionfile2
	else
		cat /home/[location]/[of]/motionfile1 > /home/[location]/[of]/motionfile2
	fi

	#Remove all lines that begine with "signal" place the output in container motionfile3
	sed '/^signal/d' </home/[location]/[of]/motionfile2> /home/[location]/[of]/motionfile3

	#Count the number of lines in motionfile 3
	S3=$(wc -l /home/[location]/[of]/motionfile3 | awk '{print $1}')
	
	#Place the last line of motionfile3 in motionfile4
	if [ $S3 -le 1 ] ; then
		cat /home/[location]/[of]/motionfile3 > /home/[location]/[of]/motionfile4
	else
		S4=$(expr $S3 - 1)
                sed "1,$S4 d" </home/[location]/[of]/motionfile3>/home/[location]/[of]/motionfile4
	fi

	#Grab the string that matches the below critereon (line contains true/false, use second string)
	S1=$(cat /home/[location]/[of]/motionfile4 | grep true | awk '{print $2}')
	S2=$(cat /home/[location]/[of]/motionfile4 | grep false | awk '{print $2}')

	#If string matches true, then screensaver is on, run motion and empty the containter files
	if [ "$S1" = "true" ] ; then
		motion
		cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile1 && cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile2 && cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile3 && cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile4

	#If string matches false then screensaver is off, wait 2 minutes, kill motion and empty the container files
	elif [ "$S2" = "false" ] ; then
		sleep 120s && killall motion
		cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile1 && cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile2 && cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile3 && cat /home/[location]/[of]/motionfile5 > /home/[location]/[of]/motionfile4
	fi
done

```

If anyone knows of a better way of accomplishing what I'm trying to accomplish or to make my script a little nicer, please post it here.

One final edit: If you use this, make sure to set the 120 in:

```
sleep 120s && killall motion
```

to a number of seconds less than seconds until your screensaver activates or it'll probably cause some problems.

---

