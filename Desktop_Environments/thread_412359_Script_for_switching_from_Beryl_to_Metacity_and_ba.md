---
title: "Script for switching from Beryl to Metacity and back?"
date: 2007-04-18
forum: Desktop Environments
---

### Post by Jhongy on 2007-04-18
Hello,

Determined to eradicate the WinXP partition on this machine, I've installed VMWare Workstation so the missus can quickly get into Windows if she needs to.

I have made a launcher for loading the WinXP VM for her, works well.

However, I use Beryl, and although it's fine normally, it really degrades the performance of the VM. I use beryl-manager to switch to metacity before booting the VM, and switch back afterwards.

Can anyone suggest a simple shell script that does

switch-to-metacity
(start vmware image) <--- I already have this line
switch-back-to-Beryl 

It must be easy, but I have no idea where to start, other than trawling through the source for beryl-manager.

[a better version of this would be the following, but I'll settle for the above!!]

if not metacity {
 x = current_manager
  switch_to_metacity
}
vmrun blah blah

if (x != metacity) {
 switch_to_manager(x)
}


I hope someone can help!!

---

### Post by Waappu on 2007-04-18
Hi

This might help

[http://ubuntuforums.org/showthread.php?t=338873&highlight=script+beryl+games](http://ubuntuforums.org/showthread.php?t=338873&highlight=script+beryl+games)

---

### Post by bashologist on 2007-04-18
Maybe something like this:
```
#!/bin/bash
if ps -e | grep metacity; then
	beryl --replace
elif ps -e | grep beryl; then
	metacity --replace
fi
```
If that detects beryl-manager too then try this maybe:
```
#!/bin/bash
if ps -e | grep "metacity$"; then
	beryl --replace
elif ps -e | grep "beryl$"; then
	metacity --replace
fi
```

---

### Post by ecschiel on 2007-10-30
I use compiz instead of beryl, and created a simple script for the same task, perhaps it's usefull for somebody. I'll try to change it to made it more ganeric, cause the way it's now only works in a combination compiz vs metacity in a default ubuntu distro + adv effects. This is the code

```

#!/bin/bash
#           runner
#
#  Sun Oct 28 07:17:37 2007
#  Copyright  2007  Enrique Schiel
#  <ecschiel@yahoo.com.ar>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Library General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA

CHANGE=0

if ps -e | grep compiz; then
    CHANGE=1
fi

if [ $CHANGE == 1 ]; then
    printf "Disabling advanced desktop efects...\n"
    /usr/bin/metacity --replace &
fi

printf "Running the game...\n"
$@ &
wait $!

if [ $CHANGE == 1 ]; then
    printf "The game is finished. Restoring advanced desktop efects...\n"
    /usr/bin/compiz --replace &
fi

```

I hope this is usefull for somebody. Any suggestions PM me.

PS: This is my firts contribution. It's my way to say "HI" to everyone :lolflag:

---

