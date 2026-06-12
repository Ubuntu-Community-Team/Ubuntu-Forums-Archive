---
title: "Feisty Filesystem"
date: 2007-04-19
forum: Desktop Environments
---

### Post by Temis on 2007-04-19
I asked the question before, but it might have been in the wrong section.
Problem: cannot  "Search for Files" in Filesystem. Click PLACES then SEARCH FOR FILES then 
LOOK IN FOLDER   I have only following options
1. Home folder (user name)
2. Desktop
3. dev (no clue what this stands for)
4. Floppy drive
5. 26.5 GB Volume (C drive)
6  76.3 GB Volume  (D drive)
    No Filesystem
I can access Filesystem via Places-Computer but not the search function.

---

### Post by Old Pink on 2007-04-19
Same situation:
[http://ubuntuforums.org/showthread.php?t=413688](http://ubuntuforums.org/showthread.php?t=413688)

I think they've done it on purpose. But there is NO use for /dev/.static/dev (where it actually links to) whatsoever.

But I liked having / (root) there?

---

### Post by Temis on 2007-04-19
So, how do I search for files in Filesystem?

---

### Post by Billy McCann on 2007-04-19
Search results > Location > Other > Filesystem

---

### Post by Medieval_Creations on 2007-04-19
You can always use the CLI.

just type:
sudo updatedb
locate [whatever file]

It will give you a long list sometimes, so you may want to dump the output to a text file for easier reading.

locate [whatever file] > search_results

---

### Post by Temis on 2007-04-19
Billy McCann wrote

"Search results > Location > Other > Filesystem"

As I wrote I do not see "Filesystem"

---

### Post by Billy McCann on 2007-04-20
[I]Temis  	Billy McCann wrote

"Search results > Location > Other > Filesystem"

As I wrote I do not see "Filesystem"[/I]

Did **Medieval_Creations**'s method work for you?

---

### Post by Temis on 2007-04-20
> **Billy McCann said:**
> [I]Temis  	Billy McCann wrote

"Search results > Location > Other > Filesystem"

As I wrote I do not see "Filesystem"[/I]

Did **Medieval_Creations**'s method work for you?

I did , the computer was crunching for a while with no result.
But I still would like to know how I could get the "Filesystem" in the search lineup?

---

### Post by Temis on 2007-04-20
Here is screen shot , maybe its clearer, I am looking for "Filesystem". Or is  a Feisty peculiarity?

---

### Post by Old Pink on 2007-04-20
Ok, here's a simple step-by-step:

[LIST=1]
[*]Click Places
[*]Click "Search for Files"
[*]Open the "Look in Folder" drop down menu
[*]Click "Other"
[*]In the "Location" entry field (automatically selected) in the dialogue that pops up, enter "/" (without ""s) so, just: /
[*]Hit enter
[*]Search. "/" is root, the equivilent of filesystem.[/LIST]Enjoy. :D

---

### Post by Temis on 2007-04-20
Thank you Old Pink.

---

