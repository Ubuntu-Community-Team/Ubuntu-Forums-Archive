---
title: "wanted: shuffle-script"
date: 2006-03-12
forum: Desktop Environments
---

### Post by maxdevis on 2006-03-12
i'm looking for a script that plays the mp3's of a map shuffled.
somebody?
python-lovers?

---

### Post by cwaldbieser on 2006-03-12
[QUOTE=maxdevis]i'm looking for a script that plays the mp3's of a map shuffled.
somebody?
python-lovers?[/QUOTE]
I'm not sure exactly what you mean by "mp3's or a map".  Is it some sort of file with entries and you want to shuffle the order?  I could write a python script to do that for you, but you'd have to be a little more specific with the details.

---

### Post by maxdevis on 2006-03-13
not or
of

i want a script that i can add to my scripts so i can right-click a map and select that script.
the script should play all the mp3's of that map shuffled.

thanks!!!

---

### Post by cwaldbieser on 2006-03-13
[QUOTE=maxdevis]not or
of

i want a script that i can add to my scripts so i can right-click a map and select that script.
the script should play all the mp3's of that map shuffled.

thanks!!![/QUOTE]
Sorry, my typo.  But I guess what I don't understand is the bit about the "map".  What is it supposed to be?  A picture of some sort?
Sorry if I am being dense, but I am not sure I get it.

---

### Post by maxdevis on 2006-03-13
hmmm, maybe we have a language-problem
map=folder
like

/boot/ = a map/folder with the files your pc needs to boot.
in my folder there are a lot of mp3-files

edit:i won't answer this post within the 12houres, because here, its allmost 00:30 in the night and i need to go to bed.
but thanks!

---

### Post by cwaldbieser on 2006-03-14
[QUOTE=maxdevis]hmmm, maybe we have a language-problem
map=folder
like

/boot/ = a map/folder with the files your pc needs to boot.
in my folder there are a lot of mp3-files

edit:i won't answer this post within the 12houres, because here, its allmost 00:30 in the night and i need to go to bed.
but thanks![/QUOTE]
OK, I think I know what you mean now.  I have the beggining of a script that could do what you want, but I will have to do a little research tomorrow to figure out how it integrates w/ Gnome (I use kubuntu).

The following script works at the command line by taking a directory and randomly playing the mp3s in that directory via xmms.  With some modification, I think I could get it to do what you want.
```

#!/usr/bin/python
 
import glob
import random
import os.path
import os
import sys

def play_random(dir):
	files = glob.glob(os.path.join(dir, "*.mp3"))
	random.shuffle(files)
	for file in files:
		print file
		os.system("xmms %s" % file)

if __name__ == "__main__":
	play_random(sys.argv[1])

```
Example usage:
```

$ python mp3shuffle.py ~/media/mp3s

```

---

### Post by Madpilot on 2006-03-14
Muine has a 'Random/Shuffle' function that can probably be fed an entire directories worth of music; I'm pretty sure Rhythymbox does too.

Unless you really need an actual seperate script to do this, there are apps that already have these functions.

---

### Post by maxdevis on 2006-03-14
[QUOTE=Madpilot]Muine has a 'Random/Shuffle' function that can probably be fed an entire directories worth of music; I'm pretty sure Rhythymbox does too.

Unless you really need an actual seperate script to do this, there are apps that already have these functions.[/QUOTE]

but i use xmms,
and can i add those functions to my nautilus script actions?

@cwaldbieser
i tried with your script but i won't work
1 part of the title of an mp3, (for example "just friends" only just) appears in the xmms screen

---

### Post by cwaldbieser on 2006-03-14
[QUOTE=maxdevis]but i use xmms,
and can i add those functions to my nautilus script actions?

@cwaldbieser
i tried with your script but i won't work
1 part of the title of an mp3, (for example "just friends" only just) appears in the xmms screen[/QUOTE]
Hmm, I should have quoted, I guess.
Try this:
```

#!/usr/bin/python
 
import glob
import random
import os.path
import os
import sys

def play_random(dir):
	files = glob.glob(os.path.join(dir, "*.mp3"))
	random.shuffle(files)
	for file in files:
		print file
		os.system('xmms "%s"' % file)

if __name__ == "__main__":
	play_random(sys.argv[1])

```
I put double quotes around the argument to xmms, so it will include spaces as part of the filename instead of breaking it into separate pieces.

Sorry I haven't had time to look at how to put this into a nautilus script.  I will try to find the time this evening.

---

### Post by cwaldbieser on 2006-03-15
OK, I think this should work:
```

#!/usr/bin/python
 
import glob
import random
import os.path
import os
import sys
import time

def play_random(dir):
	files = glob.glob(os.path.join(dir, "*.mp3"))
	if len(files) == 0:
		return
	random.shuffle(files)
	#Only way to clear the playlist is to start xmms with a file to play.
	print files[0]
	os.system('xmms "%s" 2> /dev/null &' % files[0])
	#Add the rest of the songs to the queue.
	#I found I needed to pause a second or so first to make this work.
	time.sleep(1)
	for i, file in enumerate(files):
		if i > 0:
			print file
			os.system('xmms -e "%s" 2> /dev/null &' % file)
	os.system("xmms -p 2> /dev/null")

if __name__ == "__main__":
	if len(sys.argv) < 2:
		folder = os.environ["NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"]
	else:
		folder = sys.argv[1]
	play_random(folder)

```
Put this in ~/.gnome2/nautilus-scripts and make it executable.  Then, right click on a folder, choose Scripts->the script name.  It should play all the files in the folder that match *.mp3 via xmms.

---

### Post by maxdevis on 2006-03-16
it works great!

thanks!!!!!!!
\\:D/

---

