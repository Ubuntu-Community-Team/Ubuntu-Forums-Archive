---
title: "[SOLVED] help with bash (huge nub)"
date: 2008-12-22
forum: General Help
---

### Post by knowledge_is_power on 2008-12-22
ok, so ive got a bit of a problem.  I want a script that take the output of lsusb and takes each line, chops off the first bit (so that only device name is left) and echos it.  total newb at bash and shell scripting, so please help.  I have a feeling that this is terribly wrong syntax wise, but heres what ive got, and it doesnt work.

```

#!/bin/bash
all= lsusb
numlines= lsusb | wc -l
counter=1 
while [ $counter\<$numlines ]
do
n= (( counter-- ))
echo $all | head -$counter | tail -$n | tr -d 0-9 | tail -c +21
echo "printed line $counter" 
(( counter++ ))
done
```

if i do 
```
lsusb | head -2 | tail -1 | tr -d 0-9 | tail -c +21
```
i get "Linux Foundation root hub" which is what i want.
i appear to be having trouble with the (( var-- )) and the [ conditions ] type bits.  please help.

---

### Post by Nathan Sweeney on 2008-12-22
I don't know too much about bash scripting, it's been a while since I have tried it, but I'll see if I can help

What is this supposed to do:

```
$counter\<$numlines
```

Are you trying to do less than or equal to?  I think you would want

```
while [ $counter -le $numlines ] 
```

Do you get any output at all?  Try putting in an echo as the first command after the do so that you can see if you are at least getting into the loop part.

---

### Post by knowledge_is_power on 2008-12-22
yea, heres the output, after i stuck in an echo line after the do line. e.g. now 
```
while [ $counter\<$numlines ]
do
n= (( counter-- ))
```
looks like
```
while [ $counter -le $numlines ]
do
echo "printing line $counter"
n=(( counter-- ))
```
i get nothing from that new echo, and i can't figure out why it outputs lsusb...:confused:

```
$ ./getusb.sh
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 041e:4158 Creative Technology, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
7
./getusb.sh: line 8: syntax error near unexpected token `('
./getusb.sh: line 8: `n=(( counter-- ))'

./getusb.sh: line 13: syntax error near unexpected token `done'
./getusb.sh: line 13: `done'

```

ive been browsing tutorials for a while, maybe it would be better to write a little python script... but im not sure how to get the output from lsusb into a python program.

---

### Post by Nathan Sweeney on 2008-12-22
n=$(( $counter - 1 )) might be better.  Why do you decrement the variable, and then increment it at the end of the loop?  The value of counter would remain the same at the end, and you would get an infinite loop, wouldn't you?

Also, it prints out lsusb because it is interperted as a command, don't put a space between the equal, and wrap the command with backticks (`) (on US keybords it is the key with the tilde (~) symbol) like this

```
all=`lsusb`
```

or this way works too I think

```
all="$(lsusb)"
```

---

### Post by ghostdog74 on 2008-12-22
> **knowledge_is_power said:**
> ok, so ive got a bit of a problem.  I want a script that take the output of lsusb and takes each line, chops off the first bit (so that only device name is left) and echos it.  total newb at bash and shell scripting, so please help.  I have a feeling that this is terribly wrong syntax wise, but heres what ive got, and it doesnt work.

```

#!/bin/bash
all= lsusb
numlines= lsusb | wc -l
counter=1 
while [ $counter\<$numlines ]
do
n= (( counter-- ))
echo $all | head -$counter | tail -$n | tr -d 0-9 | tail -c +21
echo "printed line $counter" 
(( counter++ ))
done
```

if i do 
```
lsusb | head -2 | tail -1 | tr -d 0-9 | tail -c +21
```
i get "Linux Foundation root hub" which is what i want.
i appear to be having trouble with the (( var-- )) and the [ conditions ] type bits.  please help.

Show at sample of your lsusb output, and describe what you want to see as output. the above code is way too ugly and long winded.

---

### Post by dagnabit dang doohickey on 2008-12-23
```
lsusb | awk '{ print substr($0,index($0,$7)) }'
```
[URL="http://www.grymoire.com/Unix/Awk.html"]
The Grymoire Awk Tutorial[/URL]

---

### Post by knowledge_is_power on 2008-12-24
holy christ.  i feel dumb.. of COURSE theres already a bash command that does exactly what i want. :P  thanks man.
so lsusb gives me 
```

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

and what i want to do is output
```
Linux Foundation 2.0 root hub
Linux Foundation 1.1 root
```
so i was trying to cycle through each line of output, put it in its own variable, and then chop off the back 21 or so characters then output it.  very unsuccessful, due mostly i think to bad syntax and lack of bash script programming experience.

EDIT:  hah, ok, i now realize how many stupid mstakes i made in the first post.  thanks to you guys heres my new script, in case ur curious

```

#!/bin/bash
all=`lsusb | grep -v "root hub"`
if [ -z $all ]
then
echo "No Devices Attached"
else
echo $all | awk '{ print substr($0,index($0,$7)) }'
fi

```

---

