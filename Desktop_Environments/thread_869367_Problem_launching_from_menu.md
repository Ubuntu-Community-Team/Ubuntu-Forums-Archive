---
title: "Problem launching from menu"
date: 2008-07-24
forum: Desktop Environments
---

### Post by TheRealWaka on 2008-07-24
In order to get around stopping and restarting compiz manually when running applications which use the 3d card, I've started using the script ecschiel provided elsewhere on the forum, which is as follows:
"
#!/bin/bash
# runner
#
# Sun Oct 28 07:17:37 2007
# Copyright 2007 Enrique Schiel
# <ecschiel@yahoo.com.ar>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU Library General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301, USA

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
fi"

I would like to re-iterate that this work is entirely that of the user ecschiel, see here for more details - [http://ubuntuforums.org/showthread.php?t=588497](http://ubuntuforums.org/showthread.php?t=588497) 
My problem is this - when I use this to launch a programme via the console, I have no problems, but when I use it in the menu, using exactly the same command, it returns the error:
[: 32: ==: unexpected operator
Does anyone have any thoughts on this problem?
Thanks,Chris

---

### Post by Tim Sharitt on 2008-07-24
What is the command you are entering in the launcher? I tried it and it worked fine. Here's the command I used:
```
/home/tsharitt/runner balazar
```

---

### Post by TheRealWaka on 2008-07-25
nocompizlaunch openarena --quiet
but I've also tried it without the argument, with the same issue, and with or without it set to launch in a terminal

---

