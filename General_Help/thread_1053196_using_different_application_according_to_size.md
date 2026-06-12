---
title: "using different application according to size"
date: 2009-01-28
forum: General Help
---

### Post by chriskin on 2009-01-28
what i want to do is to use a different application as the preferred for files of the same extension yet different sizes.
for example

i would like to use MPlayer for anime , whose size is between 300 and 400 MBs and VLC for movies whose size is a lot more than that

is that possible?

:popcorn:

---

### Post by heindsight on 2009-01-28
You could write a script like:
```

#!/bin/bash

if [ $# -eq 0 ]; then
  exit 1
fi

SIZE=$(du -m "$1" | cut -f 1)
if ((SIZE < 400)); then
  exec mplayer "$1"
else
  exec vlc "$1"
fi

```

This would get the size of the file in megabytes and execute mplayer if the file is smaller than 400MB or VLC if it's bigger.

You could put this script somewhere (say in /usr/local/bin), make it executable and then make the script your preferred application for opening movies.

You could also make the script a bit more complicated, for example the following allows you to open multiple files (opening them with mplayer if the total size is under 400MB or vlc otherwise):

```

#!/bin/bash

if [ $# -eq 0 ]; then
  exit 1
fi

SIZE=$(du -cm "$@" | tail -n 1 | cut -f 1)
if ((SIZE < 400)); then
  exec mplayer "$@"
else
  exec vlc "$@"
fi

```

---

### Post by chriskin on 2009-01-28
ok this might sound stupid, but i do not know how to do this :
" then make the script your preferred application for opening movies"

ubuntu-tweak's edit is not working :S

---

### Post by heindsight on 2009-01-28
In nautilus: 
right click on a .mpg file, 
select properties, 
go to the 'Open With' tab and click the 'Add' button.

Now click on 'Use a custom command', 
click the 'Browse' button, 
navigate to where you saved the script and double click the script,
click 'Add' 
and click 'Close'. 

From now on .mpg files will be opened using the script. You'll have to repeat the process for each file type you want to use the script for (you'll probably want to do it for .avi files too).

---

### Post by chriskin on 2009-01-28
i need it for mkv files only but i understand your logic

thank you, i will try it tonight

:popcorn:

---

