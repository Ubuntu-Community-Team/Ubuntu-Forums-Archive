---
title: "crontab woes"
date: 2011-02-12
forum: Desktop Environments
---

### Post by roguebuck on 2011-02-12
im having trouble getting crontab to run a script for me. im trying to get my wall paper to switch every 5 minutes using a simple script and feh. ive got the script itself working; it selects a random wallpaper when i run it from a terminal. the script used looks like this:

```
!/bin/bash
WALLPAPERS="/mnt/MEDIA/PICTURES/wallpapers"
ALIST=( `ls -w1 /mnt/MEDIA/PICTURES/wallpapers` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat $WALLPAPERS/.last` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > $WALLPAPERS/.last

feh --bg-fill $WALLPAPERS/${ALIST[$number]}
```

now, trying to get it to run every 5 minutes, i edited /etc/crontab by adding this line:

```
*/5 * * * * roguebuck ./home/roguebuck/.scripts/wallpaper.sh
```

but it doesnt seem to work...

what am i doing wrong? how can i get this to work?





EDIT: btw, this is all on a #! install w/ openbox. i guess that could have been pertinent info

---

### Post by Krytarik on 2011-02-13
I wouldn't run it in the global crontab at all. Add it instead to your users crontab:
- enter in the terminal
```
crontab -e
```- enter your rule:
```
*/5 * * * * /home/roguebuck/.scripts/wallpaper.sh
```- press Alt+O
- confirm with Return/Enter
- press Alt+X

Your original setup may have not worked because of this:
```
*/5 * * * * roguebuck [COLOR=Red]**.**[/COLOR]/home/roguebuck/.scripts/wallpaper.sh
```I'm actually curious if it would work the same way as when set up via user crontab.

---

### Post by asmoore82 on 2011-02-13
Your posted script is missing the `#` on the first line.

> **roguebuck said:**
> ```
ALIST=( `ls -w1 /mnt/MEDIA/PICTURES/wallpapers` )
```

You shouldn't pull a list of files this way, it breaks for filenames
with spaces or other special characters in them. Use the shell's
natural wildcard `*` ability; it's faster too!

```
wallpapers="/mnt/MEDIA/PICTURES/wallpapers"

count="0"
for file in "$wallpapers"/*
do
    alist["$count"]="$file"
    (( ++count ))
done
#no need to pull $range, we have $count
```

---

### Post by roguebuck on 2011-02-13
> **Krytarik said:**
> I wouldn't run it in the global crontab at all. Add it instead to your users crontab:
- enter in the terminal
```
crontab -e
```- enter your rule:
```
*/5 * * * * /home/roguebuck/.scripts/wallpaper.sh
```- press Alt+O
- confirm with Return/Enter
- press Alt+X

Your original setup may have not worked because of this:
```
*/5 * * * * roguebuck [COLOR=Red]**.**[/COLOR]/home/roguebuck/.scripts/wallpaper.sh
```I'm actually curious if it would work the same way as when set up via user crontab.

When i run from terminal, i need the . before the path. not sure why it would be any different from crontab.

---

### Post by Krytarik on 2011-02-14
> **roguebuck said:**
> When i run from terminal, i need the . before the path. not sure why it would be any different from crontab.
I don't, but before the script, when run without path, like this:
```
./wallpaper.sh
```
PS: Sorry for the late reply, but I somehow missed your post.

---

### Post by gmargo on 2011-02-14
The fatal flaw is the use of the image viewer **feh** without providing a **$DISPLAY** variable.

While you could supply the variable, it would be better to avoid **cron** and instead set up a script to run when you start your gnome (or kde or whatever) environment.

---

### Post by roguebuck on 2011-02-15
I tried editing my user crontab; both w/ and w/o '.' before the path to script. no workie

> **gmargo said:**
> The fatal flaw is the use of the image viewer **feh** without providing a **$DISPLAY** variable.

While you could supply the variable, it would be better to avoid **cron** and instead set up a script to run when you start your gnome (or kde or whatever) environment.

@gmargo: could you give me a little more information? you mean running a script from autostart.sh? with a 'sleep' command or something? im ignorant about scripting...but i want to learn. 

should i not be using feh? from what i can tell, it seems to be the lightest wallpaper-shower-picture-viewer-app.

---

### Post by roguebuck on 2011-02-15
> **asmoore82 said:**
> *snip*

```
wallpapers="/mnt/MEDIA/PICTURES/wallpapers"

count="0"
for file in "$wallpapers"/*
do
    alist["$count"]="$file"
    (( ++count ))
done
#no need to pull $range, we have $count
```

thanks for the headsup on the #. i was getting an error 'no file/directory /bin/bash'. lol.

could you explain what this script does; it sets the variable wallpapers, then calls that + the wildcard*. then i loose it, 'for file in' sets the variable $file?

---

### Post by roguebuck on 2011-02-17
k, i did a little tesing on that script above. im not sure how to incorporate the $count. i tried the above script:
```
wallpapers="/mnt/MEDIA/PICTURES/wallpapers"

count="0"
for file in "$wallpapers"/*
do
    alist["$count"]="$file"
    (( ++count ))
    echo $count
done

```

i see that it assigns(for lack of a better word) a number to each image. how do i pick one?

...then ill add:
```
feh --bg-fill $WALLPAPERS/${ALIST[$number]}
```

im just missing how to select one...


bump for some help? i was about to learn something!

---

### Post by asmoore82 on 2011-02-18
The (( ... )) construct is a quick and dirty way to force the shell
to do arithmetic. It has roughly the same abilities as C/C++ and
you don't have to reference variables with $ within it.

So, in this case: (( ++count )) - it's used to increment count C++ style.

The for loop is building up an array variable,
so in the end, all you have to do to get your random wallpaper is

```
"${alist["$(( RANDOM % count ))"]}"
```

---

### Post by aeiah on 2011-02-18
if crontab isnt working for me, i append the output to a file (or you could set it to email /var/mail/user)

```
*/5 * * * * /home/roguebuck/.scripts/wallpaper.sh >> ~/test.log
```

then i can see what the error is.

---

### Post by roguebuck on 2011-02-18
> **asmoore82 said:**
> The (( ... )) construct is a quick and dirty way to force the shell
to do arithmetic. It has roughly the same abilities as C/C++ and
you don't have to reference variables with $ within it.

So, in this case: (( ++count )) - it's used to increment count C++ style.

The for loop is building up an array variable,
so in the end, all you have to do to get your random wallpaper is

```
"${alist["$(( RANDOM % count ))"]}"
```

I see... I was missing the RANDOM function. ill try it out and see what happens.

> **aeiah said:**
> if crontab isnt working for me, i append the output to a file (or you could set it to email /var/mail/user)

```
*/5 * * * * /home/roguebuck/.scripts/wallpaper.sh >> ~/test.log
```

then i can see what the error is.

thanks! ill try it. ive also got the script running in a fixed while loop and a sleep command at startup. so i bypass the crontab! hehe...




update:

ITS ALIVE!!!!!! this is what ive got: (with help from you guys!)

```
#!/bin/bash
dummy=1
while dummy=1
    do
    WALLPAPERS="/mnt/MEDIA/PICTURES/wallpapers"
    ALIST=( `ls -w1 /mnt/MEDIA/PICTURES/wallpapers` )
    RANGE=${#ALIST[@]}
    let "number = $RANDOM"
    let LASTNUM="`cat $WALLPAPERS/.last` + $number"
    let "number = $LASTNUM % $RANGE"
    echo $number > $WALLPAPERS/.last

    feh --bg-fill $WALLPAPERS/${ALIST[$number]}
  sleep 240
done
```

so, it selects a random wallpaper every 4 minutes. 

but, i noticed that it still isnt working on startup, ive got to run it.

im gonna try outputting the cron to a file as suggested. Thanks to every one that helped!

---

### Post by roguebuck on 2011-02-18
dupe

---

