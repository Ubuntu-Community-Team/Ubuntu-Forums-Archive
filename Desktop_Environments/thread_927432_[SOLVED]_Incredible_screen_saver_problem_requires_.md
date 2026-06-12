---
title: "[SOLVED] Incredible screen saver problem requires imediat help"
date: 2008-09-23
forum: Desktop Environments
---

### Post by coolethan on 2008-09-23
ok so i was going through the screen savers on ubunto 7.10 and i went through the list and clicked on one called particles or something like that. in the preview screen these white letter popped up saying creating particles and at the same time froze my computer. after restarting i tried to change it but everytime i go to the screen savers thing it's allready on that same particles screen saver and freezes my computer everytime. i can't leave it running or lock the screen because then the screen saver will come on and it screws everything up. i was thinking that if i could find out where the screen saver files are located i could go in and delete that one and solve my problem but i don't have a hope in hell of finding where they are located. does anybody know where the screen saver files are located so i can go and delete that one or if there is another way let me know.

---

### Post by jludeman on 2008-09-23
[http://ubuntuforums.org/archive/index.php/t-571810.html]("http://ubuntuforums.org/archive/index.php/t-571810.html")

---

### Post by coolethan on 2008-09-23
tried some of those sugestions and they didn't work or i didn't know what they heck they were talking about. is there a way to reset ubunto to the original settings?

---

### Post by mgmiller on 2008-09-24
Open a terminal (Applications > Accessories > Terminal) and enter the following command to pop up the gconf editor:
```
gconf-editor
```Once the editor is open, on the left side click the triangle next to "apps"

Scroll down the list until you see the entry "gnome-screensaver"
Click once to highlite it.

On the right side of the screen, scroll down till you see the line called "themes", in mine, its the next to last entry.

Double click it to bring up the dialog box.

In the values area, just highlite the name particles or whatever it's called and then click remove and then ok.

You can exit the gconf editor, the change takes effect immediately.

That should return the screen saver to a selection of "none" when you run it.

Hope this helps...

---

### Post by coolethan on 2008-09-24
> **mgmiller said:**
> Open a terminal (Applications > Accessories > Terminal) and enter the following command to pop up the gconf editor:
```
gconf-editor
```Once the editor is open, on the left side click the triangle next to "apps"

Scroll down the list until you see the entry "gnome-screensaver"
Click once to highlite it.

On the right side of the screen, scroll down till you see the line called "themes", in mine, its the next to last entry.

Double click it to bring up the dialog box.

In the values area, just highlite the name particles or whatever it's called and then click remove and then ok.

You can exit the gconf editor, the change takes effect immediately.

That should return the screen saver to a selection of "none" when you run it.

Hope this helps...

thanks a lot. that worked. i actually just upgraded to 8.04 so that reset the screen saver but i had to try this out so i went and set it back to molecule. the only thing is that the screensaver never officially set itself to molecule so when i went to go remove it it was not molecule but another one that i set earlier so i removed it and that set it back to blank screen. haha i had a sticky note on the computer saying don't use molecule under any circumstances but i don't need that anymore.

---

### Post by Repgahroll on 2008-09-24
Isnt easy to hit alt+f2 then type gconf-editor?

Just a little detail :D

TY

---

### Post by coolethan on 2008-09-24
> **Repgahroll said:**
> Isnt easy to hit alt+f2 then type gconf-editor?

Just a little detail :D

TY

i'm new to linux so i didn't know anything about it.

---

### Post by mgmiller on 2008-09-25
Yes, alt/F2 would also work, but as a new user, I felt he should know where his terminal is and how to access it.

Also, try to explain how to do alt/F2....
The way you wrote it, "alt+f2" could be interpreted a number of ways. 
Do you hit the alt key, then the + key then the F2 key? 
Do you hit the alt key, then the + key then the f key then the 2 key?  
Do you try to hit alt and + and f and 2 at the same time?  

The correct answer, of course, is not obvious to someone new at this.
While holding down the alt key, press the F2 key at the top of the keyboard briefly, then let go of both keys.
Don't laugh, I have helped people in these forums with that exact problem.

In an effort to give clear and unambiguous instructions, I opted for quick directions on how to run the terminal.

That being said, alt/F2 is very handy and even helps with filling in commands as you type.  It has other uses too, as running applications and some commands from there will remain persistent after the window is closed, unlike applications or some commands run from terminal.

---

### Post by coolethan on 2008-09-25
> **mgmiller said:**
> Yes, alt/F2 would also work, but as a new user, I felt he should know where his terminal is and how to access it.

Also, try to explain how to do alt/F2....
The way you wrote it, "alt+f2" could be interpreted a number of ways. 
Do you hit the alt key, then the + key then the F2 key? 
Do you hit the alt key, then the + key then the f key then the 2 key?  
Do you try to hit alt and + and f and 2 at the same time?  

The correct answer, of course, is not obvious to someone new at this.
While holding down the alt key, press the F2 key at the top of the keyboard briefly, then let go of both keys.
Don't laugh, I have helped people in these forums with that exact problem.

In an effort to give clear and unambiguous instructions, I opted for quick directions on how to run the terminal.

That being said, alt/F2 is very handy and even helps with filling in commands as you type.  It has other uses too, as running applications and some commands from there will remain persistent after the window is closed, unlike applications or some commands run from terminal.

i'm new to linux but i'm an old computer vetaran i'm just not used to the ubuntu lay out so i was unawares of how this stuff worked though simple key press combinations don't really need any extra explanations but thanks anyways.

---

