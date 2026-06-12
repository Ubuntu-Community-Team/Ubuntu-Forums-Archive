---
title: "Scripting : Provide delegate root access (includes a handy CPU Frequency script...)"
date: 2009-03-24
forum: General Help
---

### Post by FrankT-Qc on 2009-03-24
Hi there

I have this little scripts (following) that harvests CPU frequency and gives it a cute format.

The only problem is that it has to be run as root because of access to files readable only by root.

I'd like it to work for normal users. Actually, I'm not that much interested into finding an extra solution for this special case but a general way to solve this kind of problem (running a script as a user that reads files with root only permissions)

What I've tried that didn't work :
[LIST]
[*]Using suid on the script file
[*]chmod a+r on the files (file acces is reset at reboot, it's in /sys)... Yeah, I could have a script to chmod after every boot but I don't like it !
[/LIST]


Here's the script : 

```
#!/bin/bash
#
# Prints CPU Frequency scalling
#

MAINPATH="/sys/devices/system/cpu"
ENUMFILE="$MAINPATH/online"
ROOTID=0

#Check that the script is run as root
if !( test `id -u` -eq $ROOTID ) then
	echo "Seul root peut exécuter ce script" >&2
	exit 1
fi

#Make sure the path to the info exists
if !( test -d "$MAINPATH" ) then
	echo "Impossible de trouver $MAINPATH" >&2
	exit 2
fi

#Make sure the CPU enumeration exists
if (! test -f "$ENUMFILE" ) then
	echo "Impossible de trouver l'énumération de CPU $ENUMFILE" >&2
	exit 3
fi

#Formats the CPU enumeration so it's easy to process
CPUNUMS=`cat "$ENUMFILE" | sed -r -e 's/-/ /'`

echo "Fréquence de CPU :"

#Iterate on the CPU enumeration
for CPU in $CPUNUMS
do
	#Directory for a particulare CPU
	CPUDIR="$MAINPATH/cpu$CPU/cpufreq"
	
	#Makes sur this CPU has it's directory
	if !( test -d "$CPUDIR" ) then
		echo "Impossible de trouver le sous répertoire $SUBDIR" >&2
		exit 4
	fi
		
	#Files that contain the info
	FILE="$CPUDIR/cpuinfo_cur_freq"
	GOVFILE="$CPUDIR/scaling_governor"
	
	#Makes sure the frequency file exists
	if !( test -f $FILE ) then
		echo "Impossible de trouver le fichier $FILE" >&2
		exit 5		
	fi
	
	#Makes sure the governer file exists
	if !( test -f $GOVFILE ) then
		echo "Impossible de trouver le fichier $GOVFILE" >&2
		exit 6		
	fi
	
	#Read the values
	FREQ=`cat $FILE`
	GOV=`cat $GOVFILE`
	
	#Formats (yep, I do have CPUs under 1 MHz ehehehe!)
	if ( test $FREQ -ge 1000 ) then
		FREQ=`expr $FREQ / 1000`
		UNITS="MHz"
	else
		UNITS = "KHz"
	fi
			
	echo "	CPU $CPU : $FREQ $UNITS ($GOV)"	
done

exit 0
```

Anyone has a suggestion ?

Have a nice day,
François

---

### Post by FrankT-Qc on 2009-04-09
alo ?

---

### Post by pbotros1234 on 2009-04-09
Is there a reason that your script is in /sys? If I'm not mistaken, you can't even really write to /sys, as its mounted by itself. For a script, just put it in /usr/bin or /usr/local/bin?

And make sure to run a: ```
sudo chmod +x /path/to/script
```

---

### Post by FrankT-Qc on 2009-04-09
AHAHAH 

Nah, the script is not in /sys, it reads files in /sys... and yes, it is executable...

---

