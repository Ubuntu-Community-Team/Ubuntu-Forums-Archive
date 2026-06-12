---
title: "xmame LIRC disabled"
date: 2006-11-27
forum: Gaming &amp; Leisure
---

### Post by RageAgainstThis on 2006-11-27
I'm considering building a mame cabinet powered by ubuntu.  I've got nearly all my games running on ubuntu using xmame with gxmame with the exception of area 51.  I keep receiving the error lirc disabled area51mx.chd not found.  I  have the zip file in the roms directory along with the chd in there as well.  Kinda stumped at the moment :confused: .  Any help to lead me into the right direction would be nice.

---

### Post by hikaricore on 2006-11-27
assuming you own a full sized arcade box of area 51... *cough*

you need to make a sub folder in your rom directory called area51mx (or whatever the name of the main rom zip is without the .zip) and place the chd file in there.

be careful where you step around here, most don't take kindly to touch subjects like mame chds.

--Aaron

---

### Post by hikaricore on 2006-11-27
oh and you'll need to redo your audit after this or it probably still won't find the file.

---

### Post by RageAgainstThis on 2006-11-27
I appreciate the help and i will try to watch my step around here.  Thanks Again.  :-D

---

### Post by maximilion on 2008-03-08
Aaron, you might not know this, but there are more ways for legal ownership of an arcade game than owning a big wooden box with a monitor that just happens to have a certain PCB inside.

1. Buy the PCB for a couple tenners from .jp (or ebay if you prefer overpaying :P)
2. Do the same, but ask only to send the ROMs.
3. Buy a newly manufactured multi-PCB, such as "Namco Arcade Classics", or one of those joysticks that plugs in the TV and has games on-board.

If it's OK to emulate the ROM if you own the wooden box, it is OK in all these cases as well. But I think you know all this Aaron, you know too much to be innocent ;)

Me, I'm part of a community to preserve arcade ROM sets that otherwise might go obsolete. I care too much for the technohistory to trust the original manufacturers will preserve ROM versions, documents, and schematics, because when companies change commerce dictates not wasting company resources/time on obsolete games from the 80s, no longer manufactured.

---

### Post by luca74bin on 2009-07-07
If you was a win user, probably you must unzip your files and correct the roms name in the folder...

---

### Post by m6mb3rtx on 2009-07-24
Hi there!

I had a solution that fixed me more than 1500 roms.

I use Kxmame and so if it worked for that frontend then will work for xmame.

All you need is to do is to  rename your files, i have many roms from an old Win machine that worked perfectly in Dapper but when i upgraded to Hardy they didn't work.


you need to normalize your filenames with lowercase characters.

I did it with this script patch.sh

```


#!/bin/bash
# lowercase any flilenames with uppercase chars

for file in $*
 do
 if [ -f $file ]
 then
   ucfile=`echo $file | tr [:upper:] [:lower:]`
   if [ $file != $ucfile ]
   then
     mv -i $file $ucfile
   fi     
 fi
done


```

You need to execute it in the same directory where your 'lirc diabled' roms are.

Just type:

```

find . -name '*' -exec ./patch.sh '{}' \;

```


Give it a try, i worked for me. And now i'm enjoying great old games in linux :P

---

