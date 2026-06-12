---
title: "copying from vi to clipboard does not over writes clip board buffer"
date: 2011-02-16
forum: Desktop Environments
---

### Post by tapas_mishra on 2011-02-16
Here is a situation
Situation A
---------------------------------------
I open a text file in vi
and scroll to some line
now press Esc
and :"+yy
the line gets yanked
I open gedit and Ctrl+V
and then I see the line is pasted.

Situation B
------------------------------------------------
But the same does not work for a different situation.
Suppose I opened some link in Firefox and do a Ctrl+C and in gedit I do Ctrl+V
then I can see the link getting pasted but if now I repeat the steps I
described above in Situation A
then each time on gedit I do not see the text from vi copied but the
link repeated which I do not expect
because it should have been over written by the yanked line and the
previous link of firefox should not be copied.


Is this  the correct behavior or it is a bug.

---

