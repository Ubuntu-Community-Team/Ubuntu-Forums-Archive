---
title: "No application is registered as handling this file"
date: 2009-09-02
forum: Desktop Environments
---

### Post by vishnu.patel on 2009-09-02
**C**[B][COLOR=#000000][FONT=Verdana,Arial,Tahoma][B]ould not open location 'file:///home/vishnu/Documents'
No application is registered as handling this file[/B][/FONT][/COLOR] error in ubuntu 9.04[/B] 			
 			 			 		   		 		 		I tried
Hit alt+f2, then type nautilus
When it opens, right-click on a folder, But in my case there is no any option of open with...

At right-click on a folder, i have one disabled option +Add Bookmarks and two check boxes show hidden files and show size column.

With nautilus i can open folder but i can't open folder directly places->> Documents tabs etc.

i don't know how i can solve his.


--Vishnu

---

### Post by wojox on 2009-09-02
Try this:

Go to Places > Computer

On the left click your user name

On the right right click Documents

Select Open with other application

Select Open folder

See if that works :)

---

### Post by lelamal on 2009-10-13
> **wojox said:**
> Try this:

Go to Places > Computer

On the left click your user name

On the right right click Documents

Select Open with other application

Select Open folder

See if that works :)

Oh yes, it did work! :) Many thanks, wojox! I didn't know what else to try. I was customising my Applications menu, then next thing I know I couldn't open anything from the Places menu. That's weird! Also, like Vishnu, I didn't have any *Open With* option in Properties. I'm glad I found your post. Thanks again!

---

### Post by JTwigg on 2009-11-04
I can confirm that worked for me too.
Thank you
:D

---

### Post by lelamal on 2009-11-04
> **JTwigg said:**
> I can confirm that worked for me too.
Thank you
:D

I just wanted to add that the workaround was short-lived, in my case, and other weird problems soon started to add up as a consequence. But I learnt a lesson: never mess with things you don't know well! Now I did a fresh install of Karmic, and plan to keep it as clean as possible for the time being! ;)

---

### Post by Mark V on 2009-11-08
If this happens again, try right clicking on 
'Documents', 
'Open with Other Application',
click 'use a custom command',
type in 'nautilus' without quotes,
hit the 'open' button.
If this doesn't 'stick' through a reboot,
then there is a config file somewhere that needs updating.

---

