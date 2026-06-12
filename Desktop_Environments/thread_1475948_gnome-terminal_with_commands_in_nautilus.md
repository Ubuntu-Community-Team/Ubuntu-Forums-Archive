---
title: "gnome-terminal with commands in nautilus"
date: 2010-05-07
forum: Desktop Environments
---

### Post by n.l.o on 2010-05-07
Hi.
I am trying to make a nautilus script so that I can open a special image format.
The images are actually catalogs, and to display the image I have to source some paths first.
My first and failed attempt at this looks like:
file: /home/user/.gnome2/nautilus-scripts/Display\ in\ MIRIAD

#!/bin/bash

gnome-terminal --command="mirenv; cgdisp device=/xs in=&NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

"mirenv" is a alias (set up in .bashrc to source the display program, "cgdisp")
It does not work, and since the terminal just pops up 0.5 seconds or so I can not se what is wrong.
So
1. Anybody see any obvious faults that I should correct
2. How do I get the terminal to stay after the command has be executed (sometimes cgdisp needs input)?

Cheers,
Magnus

---

### Post by kaibob on 2010-05-07
> **n.l.o said:**
> 1. Anybody see any obvious faults that I should correct
2. How do I get the terminal to stay after the command has be executed (sometimes cgdisp needs input)?

I do not have any knowledge that would be helpful with your first question. As to your second question, in general, a command in the following format will keep a terminal window open:

```
gnome-terminal --execute bash -c "ls ; bash"
```

---

### Post by n.l.o on 2010-05-09
Hey,
got it to work partially:

```
#!/bin/bash
gnome-terminal --execute bash -c "source /home/user/apps/miriad/miriad_start.sh; cgdisp device=/xs in=`pwd`/$1; bash"
```

did some of it, thanks.

Where "source" exports the path of "cgdisp" and then I run cgdisp, but I changed "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" to "$1" after some testing around.

BUT sometimes the filename (i.e. $1) is not correct, it misses the last 5 characters, could this be because some limit of the length of $1?

Cheers
Magnus

---

