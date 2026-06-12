---
title: "problem with starting firefox"
date: 2009-01-04
forum: General Help
---

### Post by cheaptrick on 2009-01-04
a pop up with the message "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system." appears everytime i try run it. 
According gnome-system-monitor, there isnt any firefox processed running in the background.

I've tried reinstalling firefox, but it doesnt help at all

---

### Post by fooman on 2009-01-04
in a terminal,  try (one at a time...try to open firefox after each one until one works):
```

sudo killall firefox

sudo killall firefox-3.1

sudo killall firefox-bin
```

---

### Post by binbash on 2009-01-04
or grep the pid with ps aux | grep firefox then kill number

---

### Post by mrkane27 on 2009-01-04
I sometimes type ALT+F2, pkill firefox

---

### Post by cheaptrick on 2009-01-04
none of the kills work..

---

### Post by DeMus on 2009-01-04
> **cheaptrick said:**
> none of the kills work..

Open System | Administration | System Monitor
Open tab Processes.
Look for an instance of Firefox, right click it and choose Kill process, and confirm.
Do this for all instances of Firefox you find in the list.
When done close System Monitor.

---

### Post by cheaptrick on 2009-01-04
there are no firefox, or mozilla whatever in the running processes to kill.

---

### Post by fooman on 2009-01-04
might want to try deleting the hidden .mozilla folder that contains your firefox config files.

**first backup your bookmarks/favorites!!**

then, open your home folder and in the toolbar click "view".  put a check next to "show hidden files"

find the .mozilla folder (your bookmarks file is in there.  look for the firefox folder and in it will be a folder that ends in .default....in there you will find the "bookmarks.html file.  copy it someplace safe)...then right click on the .mozilla folder and choose "move to trash".

try and start firefox again...see if it works.  hope that helps.

---

### Post by cheaptrick on 2009-01-04
thanks that works

---

