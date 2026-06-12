---
title: "anyone want to help a newbie install skulltag?"
date: 2010-06-17
forum: Gaming &amp; Leisure
---

### Post by dooby2016 on 2010-06-17
Hello everyone I am trying to install Skulltag (using [http://skulltag.net/wiki/Installation_for_Ubuntu](http://skulltag.net/wiki/Installation_for_Ubuntu)) but when I get to the part where I just type Skulltag I get    [I]

Skulltag v0.98b - SVN revision 2692 - SDL version
Compiled on Mar  7 2010

M_LoadDefaults: Load system defaults.
Failed to create /home/andrew/.skulltag/ directory:
Permission denied[/I]

So I did sudo skulltag instead but when I do that it just goes to 
[I]
Skulltag v0.98b - SVN revision 2692 - SDL version
Compiled on Mar  7 2010

M_LoadDefaults: Load system defaults.[/I] 

and stops. Now according to the walk through I should now have a file in my home folder named .skulltag but when I look (I have already hit ctrl+h) I cant find it and cant continue without it. Is there any chance that anyone could help I'm completely lost?

---

### Post by Grishka on 2010-06-18
umm, since you've run this with sudo, it won't see your home folder as your home folder, because by using sudo you're basically running it as a root account. so it probably created a .skulltag directory in the home folder for user root. try creating a '.skulltag' folder manually in your own home folder.

---

### Post by dooby2016 on 2010-06-18
I tried that but thank you, also i found out what it was. Basically i didnt have permissions to write to /home/andrew and i just needed to change the permissions. Thank you for your help though! ( no clue how to mark this as solved :()

---

