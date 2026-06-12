---
title: "very quick bash script counter question"
date: 2009-03-14
forum: General Help
---

### Post by Neovos on 2009-03-14
trying to make a simple bash script and the core component below:

```
#!/bin/bash

	counter=0
	while [ $counter -lt 100]; do
		echo $counter; sleep 1s
		let counter=counter+1
		done		

exit 0
```
returns this:

```
[: 7: missing ]
```

and sometimes this:
```
let: not found

```

is this a problem with my bash?

---

### Post by Neovos on 2009-03-14
The merits of walking away and coming back prevail again:

the problem was a missing space between "100" and "]", replace "lt" with "le" and I needed to get rid of the "let." Here's what worked:

```
	counter=0
	while [ $counter -le 100 ]; do
		echo $counter; sleep 1s
		counter=$(( $counter + 1 ))
		done
```

---

### Post by heindsight on 2009-03-14
> **Neovos said:**
> trying to make a simple bash script and the core component below:

```
#!/bin/bash

	counter=0
	while [ $counter -lt 100]; do
		echo $counter; sleep 1s
		let counter=counter+1
		done		

exit 0
```
returns this:

```
[: 7: missing ]
```

This is because you need a space before the ] without that space, your ] is part of the third argument "100]" to the [ command.

> **Neovos said:**
> 
and sometimes this:
```
let: not found

```

is this a problem with my bash?

Not sure why this happens, unless you sometimes interpret it with bash and sometimes with sh (linked to dash, which doesn't have let).
If you want, you can use something like
```
counter=$((counter+1))
```
instead. It should work in any POSIX compliant shell.

One piece of advice: Unless you really need bash specific features (which I think is seldom the case), it is often better (faster) to run your script with /bin/sh rather than /bin/bash -- so change the first line to:
```
#!/bin/sh
```
On Ubuntu (and many other Unix like OS's), doing this will require you to use POSIX shell syntax. You'll have to avoid bash specific syntax, but it has the advantage of being more portable, since it can then run in any POSIX compliant shell, not only in bash. On many operating systems (like Ubuntu) /bin/sh is also much faster and uses less memory than bash.

Have a look at [uwiki]DashAsBinSh[/uwiki] for more info. Also read the sh manual:
```
man sh
```
or
```
man dash
```

---

### Post by Neovos on 2009-03-14
Thank you for that, it was spot on. I learned a couple things too. 

I figure I should post the final product. Its a little bash timer that works through zenity:

```
#!/bin/sh

##----------------
##Script Name: Timer
##Description of Script: Timer that is set with user input
##Date: 20090313
#-----------------

input=$(zenity --entry --text="Enter the name of the timer, the desired time, and the units of time each separated with a space (example:tea 4 m)")

name=`echo $input | awk '{print $1}'`
time=`echo $input | awk '{print $2}'`
unit=`echo $input | awk '{print $3}'`

curtime=`date | awk '{print $4}'`

increasefactor=$(echo "${time}"/100|bc -l)

(
	counter=0
	while [ $counter -le 100 ]; do
		echo $counter; sleep "${increasefactor}""${unit}"
		counter=$(( $counter + 1 ))
	done
) | 
zenity --progress --title="$name" --text="Timer '$name' was started at $curtime. Current progress:" --percentage=0 --auto-close &&

#I frequently do the "force off" option when waiting for tasks to complete
xset dpms force on &&

zenity --info --width=350 --title="$name" --text="Timer '$name' has completed."
	
exit 0
```

---

### Post by Subban on 2009-03-28
I just wanted to say thank you for posting the final result, I assume it is ok for me to make use of it on my desktop, I am forever going to brew a cup of tea and leaving the bag in too long, I am going to  guess that given your example text I may not be alone in that ;)

---

### Post by Neovos on 2009-03-28
> **Subban said:**
> I assume it is ok for me to make use of it on my desktop, I am forever going to brew a cup of tea and leaving the bag in too long, I am going to  guess that given your example text I may not be alone in that

Absolutely; ever striving for that perfect cup of tea.

---

