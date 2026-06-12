---
title: "Even root can't kill these files??"
date: 2005-08-05
forum: Desktop Environments
---

### Post by André on 2005-08-05
Hi everybody,

i copied some music from a friend because we had to format his system.

I did this by copying from a windows system over the network at my home.

Now i have his lousy stuff on my HD and the following happens:

There are some *.wma files and i can't delete them anymore!!! I hate wma and i absolutely want them gone!

I already did some strange stuff (filename 01 Harlem's Nocturne.wma):

In Nautilus the file isn't connected to any program, i just can see the gnome foot as icon, but normal wma's play in the same directory!

When i do ls -al i get:

root@gremLin:/home/andre/Musik unsortiert/Eigene Musik/Soul/Alicia Keys/Diary of  Alicia Keys # ls -al
ls: 01 Harlem's Nocturne.wma: Keine Berechtigung
ls: 14 Samsonite Man.wma: Keine Berechtigung
insgesamt 24822
drwxr-xr-x  2 andre andre     792 1970-01-01 01:00 .
drwxr-xr-x  5 andre andre     248 1970-01-01 01:00 ..
-rwxr-xr-x  1 andre andre 2087664 2005-06-13 17:25 02 Karma.wma
-rwxr-xr-x  1 andre andre 1700406 2005-06-13 17:25 03 Heartburn.wma
-rwxr-xr-x  1 andre andre 1523288 2005-06-13 17:25 04 Titel 4.wma
-rwxr-xr-x  1 andre andre 2982260 2005-06-13 17:25 05 You Don't Know My Name.wma
-rwxr-xr-x  1 andre andre 1868518 2005-06-13 17:25 06 If I Ain't Got You.wma
-rwxr-xr-x  1 andre andre 2315816 2005-06-13 17:25 07 Diary.wma
-rwxr-xr-x  1 andre andre 2255776 2005-06-13 17:25 08 Dragon Days.wma
-rwxr-xr-x  1 andre andre 2177724 2005-06-13 17:25 09 Wake Up.wma
-rwxr-xr-x  1 andre andre 1874524 2005-06-13 17:25 10 So Simple.wma
-rwxr-xr-x  1 andre andre 1961582 2005-06-13 17:25 11 When You Really Love Someo ne.wma
-rwxr-xr-x  1 andre andre 1051976 2005-06-13 17:25 12 Feeling U, Feeling Me (Int erlude).wma
-rwxr-xr-x  1 andre andre 2108680 2005-06-13 17:25 13 Slow Down.wma
-rwxr-xr-x  1 andre andre 1433230 2005-06-13 17:25 15 Nobody Not Really (Interlu de).wma
-rwxr-xr-x  1 andre andre    2530 2005-06-13 17:25 AlbumArtSmall.jpg
-rwxr-xr-x  1 andre andre     261 2005-06-13 17:25 Desktop.ini
-rwxr-xr-x  1 andre andre    9640 2005-06-13 17:25 Folder.jpg
-rwxr-xr-x  1 andre andre   10752 2005-06-13 17:25 Thumbs.db

So, i don't even have the permission to print the properties????

When i right click on the icon and choose Properties the icon disappears but comes back when clicking refresh.

Maybe i should add that i tried to cut the files when the power was gone. So it could have something to with that??

Please, any help killing wma's is welcome!

Greetings
André

---

### Post by angkor on 2005-08-05
What happens when you do:

sudo rm [filename] ?

---

### Post by André on 2005-08-05
Hi,

thanks for your really quick reply. But as you may notice when you take a look at my post i wasn't even allowed to do a ls on the files (and i was root already).

Anyways:

root@gremLin:/home/andre/Musik unsortiert/Eigene Musik/Soul/Alicia Keys/Diary of Alicia Keys # rm 01\ Harlem\'s\ Nocturne.wma
rm: Aufruf von lstat für „01 Harlem's Nocturne.wma“ nicht möglich: Keine Berechtigung
root@gremLin:/home/andre/Musik unsortiert/Eigene Musik/Soul/Alicia Keys/Diary of Alicia Keys #

--> German: Means permission denied

andre@gremLin:~/Musik unsortiert/Eigene Musik/Soul/Alicia Keys/Diary of Alicia Keys$ sudo rm 01\ Harlem\'s\ Nocturne.wma
Password:
rm: Aufruf von lstat für „01 Harlem's Nocturne.wma“ nicht möglich: Keine Berechtigung
andre@gremLin:~/Musik unsortiert/Eigene Musik/Soul/Alicia Keys/Diary of Alicia Keys$

--> Even lstat was denied!


Any ideas??

---

### Post by André on 2005-08-05
Okay,

i cut and pasted all the files. That nearly worked.

Only three files are left. Cutting and pasting gave me a total freeze of the system... Nearly, i still could use the system but nothing worked and gave no reaction. I was able to move windows around but the content of the windows weren't refreshed anymore.

Please help!!

---

### Post by angkor on 2005-08-05
I have no idea why these files cannot be removed by root. They must be corrupted beyond repair ;)

You could try deleting the files with a Livecd like knoppix,  and see if that works. Maybe someone a bit more knowledgeable could help you out.

---

### Post by Omnios on 2005-08-05
Not shure if you know this but in terminal does not like spaces my music must be "My Music" or was it 'My Music' this sounds a bit strange to me as this usualy states no such file but you version might be a bit different worth a try though. At least you will be able to sudo rm

---

### Post by André on 2005-08-05
Hi everybody,

here comes the answer. The early powering off corrupted my reiserfs partition.

A simple boot up with my just arrived Ubuntu CDs (thanks Mr. Shuttleworth :-)) followed by a nice 'reiserfschk --rebuild-tree /dev/hda5' brought the system out of the fubar state and up and running again :-)

Goodbye wma's, greetings and thanks for the answers
André

P.S.:
@Omnios:
Use the backslash notation for directories and white spaces are okay.

---

