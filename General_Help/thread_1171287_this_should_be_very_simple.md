---
title: "this should be very simple"
date: 2009-05-27
forum: General Help
---

### Post by mr_gourami on 2009-05-27
a friend wrote me this program. and set it up in my computer. well i have a new computer and i accidentally destroyed the program. but i did save the code. but i dont know what to do with this? 

i think i just need to save the bottom code as a program but i dont know how or where to save it to. It used to run out of the terminal.



#!/bin/bash
#
# Encode DVD files to mpeg4 for Madison
#
# Usage: ripdvd <name> <nr_of_titles>

if [ $# -ne 2 ];
then
echo "Usage: ripdvd <name> <nr_of_titles>"
exit 0
fi

counter=1

while [ "$counter" -le "$2" ];
do
nice -n 19 mencoder dvd://"$counter" -o "$1"_"$counter".avi -oac mp3lame -ovc xvid -lameopts preset=medium:vol=7 -xvidencopts turbo***=1:bitrate=-716800:threads=2 -alang en
nice -n 19 mencoder dvd://"$counter" -o "$1"_"$counter".avi -oac mp3lame -ovc xvid -lameopts preset=medium:vol=7 -xvidencopts pass=2:bitrate=-716800:threads=2 -alang en
counter=$(( $counter + 1 ))
done

---

### Post by Yellow Pasque on 2009-05-27
Paste all the code into a text file, save it as ripdvd, and make the file executable.

---

### Post by mr_gourami on 2009-05-27
thanks. but i think i need to save it under /bin or /usr/bin or somethin like that. and everytime i try to save it says i dont have permission. how do i save it with permission?

---

### Post by konqueror7 on 2009-05-27
try using the 'cp' or 'mv' command with 'sudo',
```
sudo cp <file> <destination>
sudo mv <file> <destination>
```
for more info,
```
man cp
man mv
```

---

### Post by mr_gourami on 2009-05-27
ok i was able to copy it but... 
in a terminal i get...

madison@madison-desktop:~$ ripdvd
bash: /usr/bin/ripdvd: Permission denied
madison@madison-desktop:~$ sudo ripdvd
sudo: ripdvd: command not found

im confused. i saved it in /usr/bin was that not right?

---

### Post by Legace on 2009-05-27
> **mr_gourami said:**
> ok i was able to copy it but... 
in a terminal i get...

madison@madison-desktop:~$ ripdvd
bash: /usr/bin/ripdvd: Permission denied
madison@madison-desktop:~$ sudo ripdvd
sudo: ripdvd: command not found

im confused. i saved it in /usr/bin was that not right?

Browse to /usr/bin with nautlius and make sure the file exists.

Also make sure the file is executable:
```
sudo nautilus /usr/bin
```
Find ripdvd. Right-click, select Properties, select Permissions tab, and check option to make file executable..
Then try again.

---

### Post by mr_gourami on 2009-05-27
AHH!! THAnk you!! 

and for anyone else this is does a great job of ripping! very idiot proof
(once you figure out how to make it start he he..)

---

### Post by SOULRiDER on 2009-05-27
You should place the file in
```
/usr/bin/
```
and not in ```
/bin
```

---

