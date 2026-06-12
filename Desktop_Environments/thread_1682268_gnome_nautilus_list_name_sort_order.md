---
title: "gnome nautilus list name sort order"
date: 2011-02-05
forum: Desktop Environments
---

### Post by rhdinah on 2011-02-05
In nautilus the name sort order is not according to what I would expect. There seems to be a bit of what I'd call slop in the sort process. By slop I mean that the sort order is not the same I'd get from an 'ls' command. Instead it drops spaces and other characters like '-' in the sort. This causes discrepancies when using the command line in a terminal and looking at a nautilus list concurrently ... and times being quite frustrating. I cannot find a setting anywhere where this can be changed. Does anyone have a better idea where to find such a setting if one exists? Actually IMHO I can't see why one would want a sort that isn't character-by-character anyway, but as the default behaviour it's even more odd ... especially in *nix ... IMHO ... :p

---

### Post by asmoore82 on 2011-02-05
It is typically sorting in command-line tools that is considered a little off.
Nautilus attempts a more "user-friendly" sort "in plain English" -
or really - in plain whichever language is in "/etc/default/locale"

If you really want naive sorting, you can set "LC_COLLATE=C" in this file.

But, true "character-by-character" sorting is a "be careful what you wish for"
situation. If you set LC_COLLATE=C you will see that the sort becomes case
sensitive - capital letters will always sort ahead of lowercase letters.

Numbers are also a huge problem with "character-by-character" sorting:
"1, 2, 3, 04, 11, 22, 33, 0400" will become "04, 0400, 1, 11, 2, 22, 3, 33"

P.S. I tested this and the strangest thing -
nautilus always has a bit of a mind of its own -
It still does numbers fine with LC_COLLATE=C but
`ls` becomes naive as above^.

---

### Post by rhdinah on 2011-02-12
> **asmoore82 said:**
> It is typically sorting in command-line tools that is considered a little off.
Nautilus attempts a more "user-friendly" sort "in plain English" -
or really - in plain whichever language is in "/etc/default/locale"

If you really want naive sorting, you can set "LC_COLLATE=C" in this file.

But, true "character-by-character" sorting is a "be careful what you wish for"
situation. If you set LC_COLLATE=C you will see that the sort becomes case
sensitive - capital letters will always sort ahead of lowercase letters.

Numbers are also a huge problem with "character-by-character" sorting:
"1, 2, 3, 04, 11, 22, 33, 0400" will become "04, 0400, 1, 11, 2, 22, 3, 33"

P.S. I tested this and the strangest thing -
nautilus always has a bit of a mind of its own -
It still does numbers fine with LC_COLLATE=C but
`ls` becomes naive as above^.

Thanks for your answer and pointers. Coming from the command line world myself, which has set the precedent for *nix systems, I wouldn't consider them at all 'off' or naive. Personally I consider most *every* command line tool as having proved itself over the years as they've all passed through a plethora of standards committees and withstood the test of time among techies and gurus.

As far as leading zeroes corrupting the sort ... they do not! If they are part of the string of characters that they are ... they are characters not numbers ... albeit all characters are numbers at their byte-level obviously.

Dumbing things down to make things 'user-friendly' rather irks me ... much like the 'Macintosh mode' in Windows where they strip the file extensions off the file name.

Clearly there should be a sort order choice in Preferences under Edit or sort order menu item under View for nautilus.

---

### Post by asmoore82 on 2011-02-12
> **rhdinah said:**
> As far as leading zeroes corrupting the sort ... they do not!
They don't for nautilus, they do for `ls`. Or vice-versa depending on your preference.
The fact is that nautilus and `ls` handle sorting of numbers differently.

> **rhdinah said:**
> Dumbing things down to make things 'user-friendly' rather irks me ... much like the 'Macintosh mode' in Windows where they strip the file extensions off the file name.
I don't care for "dumbing things down" at all either.
But, I do not consider changing the sort order of "1, 11, 111, 2, 22, 222, 3, 33"
to "1, 2, 3, 11, 22, 33, 111, 222" a case of "dumbing things down" 

> **rhdinah said:**
> Clearly there should be a sort order choice in Preferences under Edit or sort order menu item under View for nautilus.
I wouldn't complain about that 1 bit. But is it a "feature request," not a "bug report."

---

### Post by Nosugrof on 2012-06-28
> **asmoore82 said:**
> They don't for nautilus, they do for `ls`. Or vice-versa depending on your preference.
The fact is that nautilus and `ls` handle sorting of numbers differently.


I don't care for "dumbing things down" at all either.
But, I do not consider changing the sort order of "1, 11, 111, 2, 22, 222, 3, 33"
to "1, 2, 3, 11, 22, 33, 111, 222" a case of "dumbing things down" 


I wouldn't complain about that 1 bit. But is it a "feature request," not a "bug report."

I'm sure it was done in the spirit of being user friendly and with the best intention but I agree that it's dumbing down the software. I disagree with any software that tries to  guess what I want rather than just doing what I asked for. If I want a list of files then give me the list - not some arbitrary interpretation of what someone thinks the list should look like.

---

### Post by coffeecat on 2012-06-28
Old thread closed. Please do not bump old threads.

---

