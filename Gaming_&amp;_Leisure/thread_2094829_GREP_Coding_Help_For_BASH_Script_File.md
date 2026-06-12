---
title: "GREP Coding Help For BASH Script File"
date: 2012-12-14
forum: Gaming &amp; Leisure
---

### Post by mark bower on 2012-12-14
I am working towards disabling mouse emulation of USB rc plane controller; when the controller is plugged in, it interferes with the mouse pointer.  I have successfully disabled per post #34 in the following link:  

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470)

However, as noted by post #36 in the link, the option numbers can change with each boot, thus to facilitate disabling, a script is in order that can be launched when necessary.  1st I run xinput list per below to obtain the controller name.  In this case, the line "WAILLY PPM            id=12	[slave  pointer  (2)]
" is the one of interest.  WAILLY PPM is my controller (and in this case its id =12, but it has also been 13).

rocky@mark:~$ xinput list
&#9121; Virtual core pointer                	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer       	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Mouse                id=13	[slave  pointer  (2)]
&#9116;   &#8627; WAILLY PPM                         id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                  id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard       id=5	[slave  keyboard (3)]
    &#8627; Power Button                       id=6	[slave  keyboard (3)]
    &#8627; Power Button                     	id=7	[slave  keyboard (3)]
 
    &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=8	[slave  keyboard (3)]
    &#8627; WAILLY PPM (keys)                  id=11	[slave  keyboard (3)]

Now I want to adopt the script code in post #36 in the link.  I substitute the name of my controller;  the script generates the error:  "grep: PPM: No such file or directory"

NAME="WAILLY PPM"
ids=$(xinput list | grep $NAME | grep -o -e "id=.." | xargs | sed "s/id=//g")
for id in $ids; do
    echo "Disabling Mouse/Key events for ID $id"
    xinput set-prop $id "Generate Mouse Events" 0
    xinput set-prop $id "Generate Key Events" 0
done

I would appreciate a suggestion to where the syntax is in error.  I looked at a lot of grep stuff, but could not determine the problem.

mark bower

---

### Post by steeldriver on 2012-12-14
just glancing at your code the most obvious thing is it is probably word-splitting your $NAME variable (because it contains whitespace)  - so you need to quote it:-

```
 ids=$(xinput list | grep [COLOR=Red]**"**[/COLOR]$NAME[COLOR=Red]**"**[/COLOR] | grep -o -e "id=.." | xargs | sed "s/id=//g")
```Just fyi it is bad practice to use all upper case names for your bash variables

... there may be other issues, didn't really check

---

### Post by mark bower on 2012-12-14
Thank you.  That was the problem, when corrected to "$NAME" the code now generates:

Disabling Mouse/Key events for ID 12
Disabling Mouse/Key events for ID 11
property Generate Mouse Events doesn't exist, you need to specify its type and format
property Generate Key Events doesn't exist, you need to specify its type and format

So, I need to play with the script a bit more and probably return for more help.

---

### Post by oldrocker99 on 2012-12-15
It's proper etiquette to amend the title with [SOLVED] here, I believe;).

---

### Post by mark bower on 2012-12-15
O.K. The following code when executed "delinks" the mouse pointer from joystick movements.  The sequence: 1)open a terminal, 2)enter the script file on the cmd line, 3)plug in the rc-controller(see the mouse move to left), 4)with some skill get the uncooperative mouse cursor to pass over the terminal screen and click on it to make it active, 5)hit return to execute the script.  And voilla, the cursor returns to normal behavior.

```
#!/bin/bash
#file:  script_rccontroller.sh
#use to disable mouse emulation from controller sticks(joysticks)
#get NAME for controller from xinput list

NAME='WAILLY PPM'

ids=$(xinput list | grep  "$NAME" | grep -o -e "id=.." | xargs | sed "s/id=//g")
for id in $ids; do
    echo "Disabling Mouse/Key events for ID $id"
    xinput set-prop $id "Generate Mouse Events" 0
    xinput set-prop $id "Generate Key Events" 0
done
```

But even tho the code works, I get the two error msgs:
property Generate Mouse Events doesn't exist, you need to specify its type and format
property Generate Key Events doesn't exist, you need to specify its type and format

Can anyone suggest the syntax to eliminate these error msgs.  And again, please refer to the link (item 36) in my 1st post to see what I am trying to adapt for my use.

---

### Post by mark bower on 2012-12-16
Following are now two scripts which work without generating error msgs.  The 1st is the one discussed so far.  The 2nd one works and seem to make the change permanent - I could not get back to a condition where the USB joysticks affected the mouse cursor.  And of course, this is just fine since it is the condition I want.  But it would be interesting to know where the change took place.  Also, I was hoping to use the 2nd option on a second computer I have, but USB joystick activity was already separated from the mouse cursor.  I do not know why as I had not yet looked at the separation issue on the 2nd computer.

Option 1 (do for each boot):
```

#!/bin/bash
NAME="WAILLY PPM"
ids=$(xinput list | grep $NAME | grep -o -e "id=.." | xargs | sed "s/id=//g")
for id in $ids; do
   echo "Disabling Mouse/Key events for ID $id"
   xinput set-prop $id "WAILLY PPM" "Generate Mouse Events" 0
   xinput set-prop $id "WAILLY PPM" "Generate Key Events" 0
done
```

Option 2 (which seems to make a permanent change):
```
#!/bin/bash
NAME='WAILLY PPM'

ids=$(xinput list | grep  "$NAME" | grep -o -e "id=.." | xargs | sed "s/id=//g")
for id in $ids; do
    echo "Disabling Mouse/Key events for ID $id"
    xinput set-prop $id "WAILLY PPM" "Device Enabled" 0
done
```

---

