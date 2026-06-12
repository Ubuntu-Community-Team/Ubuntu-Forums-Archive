---
title: "Gnome Desktop Issues?"
date: 2007-04-25
forum: Desktop Environments
---

### Post by orb9220 on 2007-04-25
Looking for confirmation of these annoyances and to find solutions if possible.

1) Panel Handles - They are really ugly and detract from theming.

2) Gnome dialogs always open up squished and are alot of times nearly unusable until you manually resize them.

3) Gnome open dialog does not show .files or .folders this is also irritating to know end. Example I have gedit open and then some tut says to open .conkyrc from your home directory. Can I do that ? NO! 

4) Just recent? In feisty if I open nautilus and go to Computer then I see Floppy,CD-rom drive,Filesystem.  If I open a gksudo nautilus then go to computer I only see Filesystem. Bug? I would think sudo would give you more access.

That is it for now. If you can think of some I have not listed feel free to post them here.

Please if you have solutions or workarounds to these I would love to hear them.

---

### Post by llamakc on 2007-04-25
*3) Gnome open dialog does not show .files or .folders this is also irritating to know end. Example I have gedit open and then some tut says to open .conkyrc from your home directory. Can I do that ? NO!*

Yes you can. Open Gedit and try opening a dot-file. Will you see them in the graphical browser thingy? Not by default. But you can ALREADY type in .conkyrc and it will most assuredly open the file for you.

So your issue is not that the file can not be opened, it is that the 'open file' dialog does not show hidden files. You should look for a solution to THAT problem. Me? I use a text editor from within a terminal. `ls -a` is awesome.

PS: the phrase is "to no end".

---

### Post by llamakc on 2007-04-25
Wow. Google and first hit:

[http://lascribe.net/2005/12/08/8/](http://lascribe.net/2005/12/08/8/)

 right-click in the file listing inside the “open file” dialogue and choose “show hidden files”.

---

### Post by orb9220 on 2007-04-25
Thanks I have never right click a file in the dialog and seen that before. 

Thanks for the info. Always willing to learn something new.

---

### Post by orb9220 on 2007-04-27
Thanks to llamakc issue 3 resolved due to user's ignorance.

Anybody know about the other issue's?

---

### Post by tgoose on 2007-04-30
> **orb9220 said:**
> Thanks to llamakc issue 3 resolved due to user's ignorance.

Anybody know about the other issue's?

I wouldn't say that's just user ignorance if at least two people had to search on the Internet to find out how to do such a simple task (although I was hiding them rather than showing them, so I guess I must have already done it once in the distant past!)

I think this needs to be made more obvious/easier to find.

For the other issues I don't have a solution but I can reproduce at least 4. Is this perhaps because they are mounted as the user rather than as root? I don't know that that would make a difference, but it's the only thing that sprang to mind.

---

### Post by jfinkels on 2007-04-30
I don't know if this has something to do with it, but when I do a "gksudo nautilus" and view the root directory, the only folders I can see initially are /home and /media. I need to press <Ctrl>+<h> to enable hidden files before I can see the rest of the folders in the directory. Strange but true. I don't know why that happens either, seems counter-intuitive and is somewhat confusing.

---

### Post by Eric Layne on 2007-04-30
+1 for item #2 ( Gnome dialogs always open up squished and are alot of times nearly unusable until you manually resize them.)

How about the Trash Can bug: Trash is full of items, yet a trashcan icon rollover with the mouse shows Trash as empty and thus cannot be emptied via right-click.

---

