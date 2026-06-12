---
title: "Nice Wallpaper Randomizer Script"
date: 2010-08-12
forum: Desktop Environments
---

### Post by Wisp558 on 2010-08-12
So I got bored today, and decided that my desktop just wasn't interesting enough. So I wrote this script. It'll cycle through random .png and .jpg images in a directory. Here's the script.

```

#!/bin/bash

DIR=/home/wisp/Wallpapers
FLOOR=1
RANGE=`ls -1 "$DIR"/*.jpg "$DIR"/*.png | wc | awk '// {print $1}'`

number=0

while [ 1 -eq 1 ]; do
	
	number=$RANDOM
	while [ "$number" -le $FLOOR ]; do
  		number=$RANDOM
	done
	let "number %= $RANGE"  # Scales $number down within $RANGE.
	COUNTER=1
	for X in "$DIR"/*.jpg "$DIR"/*.png
	do
		if [ $number -eq $COUNTER ]; then
			feh --bg-scale "$X"
		fi
	COUNTER=$(($COUNTER+1))
	done
	COUNTER=1
	sleep 2m
done

```

The observant will note that I use feh to change the background. If you use the standard GNOME desktop, you will need to replace 

```
feh --bg-scale "$X"
```

with 

```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$X"
```

You will also need to change $DIR to wherever your wallpapers are, and you can change the 'sleep 2m' line to whatever you feel like keeping your wallpapers for.

To run it, just copy the code into a text file, name it, say, wallpaperrandomizer.sh. Then you just need to run chmod +x wallpaperrandomizer.sh, and run the file. ( ./wallpaperrandomizer.sh & disown )


Though it doesn't do recursive scanning, this script will tolerate spaces! Neat!

Enjoy.

---

### Post by ubunterooster on 2010-08-12
Sweet!

---

### Post by Wisp558 on 2010-08-12
Well, let me know how it works out for you... I just wrote it today, so there could still be some bugs hiding in it (god forbid).

Oh wait, just noticed one. the $X in the feh line needs to become "$X", to fix the space-ignoring.

Anyways, yeah! Let me know!

---

### Post by ubunterooster on 2010-08-12
> **Wisp558 said:**
> Well, let me know how it works out for you... I just wrote it today, so there could still be some bugs hiding in it (god forbid).

Oh wait, just noticed one. the $X in the feh line needs to become "$X", to fix the space-ignoring.

Anyways, yeah! Let me know!
try editing the first post to correct bug.

---

### Post by Wisp558 on 2010-08-12
> **ubunterooster said:**
> try editing the first post to correct bug.

You're right, of course. Forgive me, my mind is a little scattered from a session of sorting out bash's peculiar eccentricities.

---

