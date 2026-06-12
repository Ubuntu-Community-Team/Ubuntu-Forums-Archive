---
title: "Bash script to generate backgrounds.xml for gnome"
date: 2009-12-03
forum: Desktop Environments
---

### Post by ozhoo on 2009-12-03
I like the automated wallpaper switching in gnome.

Here is a cli script that generates an xml which can be consumed by the backgrounds config.  Full pathnames to the background folders are required.

```

#!/bin/bash
# gnome-backgrounds-xmlgen.sh
#
# usage:./gnome-backgrounds-xmlgen.sh background_dir_1 background_dir_2 background_dir_3
#
# description: simply generate a backgrounds xml that can be consumed by gnome's background configuration
#
# authors: ozhoo & browner @ ubuntuforums.org
#
# note: only looks for .JPG and .jpg files

# output file
FILENAME=backgrounds.xml

# start time (any time in the past works)
YEAR=2009
MONTH=04
DAY=02
HOUR=00
MINUTE=00
SECOND=00

# time to show background (seconds)
WALLDURATION=900.0

# transition time (seconds)
TRANSDURATION=5.0

# script specifics
DIRS=$*
T1="echo -e \t"
T2="echo -e \t\t"

echo "<background>" > "$FILENAME"
${T1}"<starttime>" >> "$FILENAME"
${T2}"<year>${YEAR}</year>" >> "$FILENAME"
${T2}"<month>${MONTH}</month>" >> "$FILENAME"
${T2}"<day>${DAY}</day>" >> "$FILENAME"
${T2}"<hour>${HOUR}</hour>" >> "$FILENAME"
${T2}"<minute>${MINUTE}</minute>" >> "$FILENAME"
${T2}"<second>${SECOND}</second>" >> "$FILENAME"
${T1}"</starttime>" >> "$FILENAME"

get_first()
{
    for d in $DIRS; do
        find "$d"|grep -i .jpg|while read j; do
            echo "$j"
            break
        done
        break
    done
}

FIRST="$(get_first)"

${T1}"<static>" >> "$FILENAME"
${T2}"<duration>${WALLDURATION}</duration>" >> "$FILENAME"
${T2}"<file>${FIRST}</file>" >> "$FILENAME"
${T1}"</static>" >> "$FILENAME"
${T1}"<transition>" >> "$FILENAME"
${T2}"<duration>${TRANSDURATION}</duration>" >> "$FILENAME"
${T2}"<from>${FIRST}</from>" >> "$FILENAME"

for d in $DIRS; do
    find "$d"|sort -R|grep -i .jpg|while read j; do
        if [ "$j" == "$FIRST" ]; then
            continue
        else
            ${T2}"<to>${j}</to>" >> "$FILENAME"
            ${T1}"</transition>" >> "$FILENAME"
            ${T1}"<static>" >> "$FILENAME"
            ${T2}"<duration>${WALLDURATION}</duration>" >> "$FILENAME"
            ${T2}"<file>${j}</file>" >> "$FILENAME"
            ${T1}"</static>" >> "$FILENAME"
            ${T1}"<transition>" >> "$FILENAME"
            ${T2}"<duration>${TRANSDURATION}</duration>" >> "$FILENAME"
            ${T2}"<from>${j}</from>" >> "$FILENAME"
        fi
    done
done

${T2}"<to>${FIRST}</to>" >> "$FILENAME"
${T1}"</transition>" >> "$FILENAME"
echo "</background>" >> "$FILENAME"

```Here it is in a form consumable by nautilus.  

```

#!/bin/bash
# 
# Place this in your ~/.gnome2/nautilus-scripts directory
#
# authors: ozhoo & browner @ ubuntuforums.org
#
# note: only looks for .JPG and .jpg files

# current location
CWD="$(pwd)"

# output file
FILENAME=backgrounds.xml

# start time (any time in the past works)
YEAR=2009
MONTH=04
DAY=02
HOUR=00
MINUTE=00
SECOND=00

# time to show background (seconds)
WALLDURATION=900.0

# transition time (seconds)
TRANSDURATION=5.0

# script specifics
DIRS=$*
T1="echo -e \t"
T2="echo -e \t\t"

echo "<background>" > "$FILENAME"
${T1}"<starttime>" >> "$FILENAME"
${T2}"<year>${YEAR}</year>" >> "$FILENAME"
${T2}"<month>${MONTH}</month>" >> "$FILENAME"
${T2}"<day>${DAY}</day>" >> "$FILENAME"
${T2}"<hour>${HOUR}</hour>" >> "$FILENAME"
${T2}"<minute>${MINUTE}</minute>" >> "$FILENAME"
${T2}"<second>${SECOND}</second>" >> "$FILENAME"
${T1}"</starttime>" >> "$FILENAME"

get_first()
{
    for d in $DIRS; do
        find "${CWD}/${d}"|grep -i .jpg|while read j; do
            echo "$j"
            break
        done
        break
    done
}

FIRST="$(get_first)"

${T1}"<static>" >> "$FILENAME"
${T2}"<duration>${WALLDURATION}</duration>" >> "$FILENAME"
${T2}"<file>${FIRST}</file>" >> "$FILENAME"
${T1}"</static>" >> "$FILENAME"
${T1}"<transition>" >> "$FILENAME"
${T2}"<duration>${TRANSDURATION}</duration>" >> "$FILENAME"
${T2}"<from>${FIRST}</from>" >> "$FILENAME"

for d in $DIRS; do
    find "${CWD}/${d}"|sort -R|grep -i .jpg|while read j; do
        if [ "$j" == "$FIRST" ]; then
            continue
        else
            ${T2}"<to>${j}</to>" >> "$FILENAME"
            ${T1}"</transition>" >> "$FILENAME"
            ${T1}"<static>" >> "$FILENAME"
            ${T2}"<duration>${WALLDURATION}</duration>" >> "$FILENAME"
            ${T2}"<file>${j}</file>" >> "$FILENAME"
            ${T1}"</static>" >> "$FILENAME"
            ${T1}"<transition>" >> "$FILENAME"
            ${T2}"<duration>${TRANSDURATION}</duration>" >> "$FILENAME"
            ${T2}"<from>${j}</from>" >> "$FILENAME"
        fi
    done
done

${T2}"<to>${FIRST}</to>" >> "$FILENAME"
${T1}"</transition>" >> "$FILENAME"
echo "</background>" >> "$FILENAME"

```CHEERS

---

### Post by Pusi85 on 2009-12-03
Hey, man!

Great little script! Already started using it! =)
Thanks much!

Pusi85 form HUNGARY

---

### Post by ozhoo on 2009-12-04
@pusi85 cheers!

> **Pusi85 said:**
> Hey, man!

Great little script! Already started using it! =)
Thanks much!

Pusi85 form HUNGARY

---

### Post by BrowneR on 2010-03-29
Many thanks ozhoo! Great little script :)

---

### Post by BrowneR on 2010-03-29
> **BrowneR said:**
> Many thanks ozhoo! Great little script :)

Just wanted to say I also modified the two "find" lines in your script to give me a random sorted list instead of alphabetical. This way I can have one folder of photographs and one folder of computer generated images and get a nice mixture of the two when it is displayed.

In case anyone else is interested just change the two find lines so they read as follows:

```

find "$d"|sort -R|grep -i .jpg|while read j; do

```

Cheers,
Chris

---

### Post by AnThoMan on 2010-06-11
Hi,

I am totally new to the Ubuntu scene, recently upgraded from Windows 7 whereby I had this ability to automatically change backgrounds.

I have tried numerous times to do this but coding is just not in my blood.


Can someone please explain how to set a specific folder of photos for this script?


All the best,

Andrew

---

### Post by ozhoo on 2010-06-11
@browner Sweet. This makes more sense.  Edited original post & added your input

> **BrowneR said:**
> Just wanted to say I also modified the two "find" lines in your script to give me a random sorted list instead of alphabetical. This way I can have one folder of photographs and one folder of computer generated images and get a nice mixture of the two when it is displayed.

In case anyone else is interested just change the two find lines so they read as follows:

```

find "$d"|sort -R|grep -i .jpg|while read j; do

```

Cheers,
Chris

---

### Post by ozhoo on 2010-06-11
@AnThoMan

Comment out the line DIRS=$*

and replace with 

DIRS=/path/to/your/backgrounds

> **AnThoMan said:**
> Hi,

I am totally new to the Ubuntu scene, recently upgraded from Windows 7 whereby I had this ability to automatically change backgrounds.

I have tried numerous times to do this but coding is just not in my blood.


Can someone please explain how to set a specific folder of photos for this script?


All the best,

Andrew

---

### Post by mexicanseaf00d on 2010-06-18
this works great, thanks a lot!

---

### Post by Boondoklife on 2010-06-18
Ever thought of making a nautilus script out of this? You could then just click and highlight the files/folders and generate the file without the command line.

---

### Post by ozhoo on 2010-06-18
@Boondoklife 

I've got it working as a nautilus script with some minor changes.  However this will only work with multiple folders if they are siblings of the same parent folder structure.  Selected folders are expanded as arguments to the nautilus sript without their full paths.

Here is the Diff. 

11a12,14
> # current location
> CWD="$(pwd)"
> 
47c50
<         find "$d"|grep -i .jpg|while read j; do
---
>         find "${CWD}/${d}"|grep -i .jpg|while read j; do
66c69
<     find "$d"|sort -R|grep -i .jpg|while read j; do
---
>     find "${CWD}/${d}"|sort -R|grep -i .jpg|while read j; do


> **Boondoklife said:**
> Ever thought of making a nautilus script out of this? You could then just click and highlight the files/folders and generate the file without the command line.

---

### Post by lvhuiwei on 2010-07-02
really great!

thanks!

---

### Post by rulesmaster on 2010-12-26
i've been researching all around the net, learning how to parse files to generate an xml by bash and all of that, that i don't know yet, and researching for more info and tuts, stumbled with the very exact same thing that i wanted to acomplish in the first place.

Works marvelous, and i'm so going to learn so much about shell scripting with this...

Kudos man, you rule

---

### Post by ozhoo on 2011-02-20
Very cool.  I should post a Python version

> **rulesmaster said:**
> i've been researching all around the net, learning how to parse files to generate an xml by bash and all of that, that i don't know yet, and researching for more info and tuts, stumbled with the very exact same thing that i wanted to acomplish in the first place.

Works marvelous, and i'm so going to learn so much about shell scripting with this...

Kudos man, you rule

---

### Post by guyverix on 2011-03-03
Is there any way that you would be able to pass 2 images to Gnome and have them both display as a background image?  I know it would look horrible on a single monitor system, but I am trying to find a decent solution to getting two backgrounds on my different monitors.

---

### Post by ozhoo on 2011-03-05
That seems like something that I could do yes.  I believe you could find something that already exists to accomplish this though. Maybe in this thread you'll find a solution [http://ubuntuforums.org/showthread.php?t=223061](http://ubuntuforums.org/showthread.php?t=223061)

> **guyverix said:**
> Is there any way that you would be able to pass 2 images to Gnome and have them both display as a background image?  I know it would look horrible on a single monitor system, but I am trying to find a decent solution to getting two backgrounds on my different monitors.

---

