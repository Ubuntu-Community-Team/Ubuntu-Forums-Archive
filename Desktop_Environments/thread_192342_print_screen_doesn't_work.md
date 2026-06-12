---
title: "print screen doesn't work"
date: 2006-06-08
forum: Desktop Environments
---

### Post by mluu510 on 2006-06-08
my print screen keyboard button doesn't work. i already configured it in keyboard shortcut. the only way for me to make a screenshot is to run the app but that stops me from taking a screenshot when i need to. can anyone help me out?

---

### Post by aysiu on 2006-06-08
I'm going to answer you in [the other thread you posted about this.](http://www.ubuntuforums.org/showthread.php?t=192342)

**Edit**: Never mind. I guess the two threads got merged.

---

### Post by aysiu on 2006-06-08
Well, let's say if the problem is the key itself or associating the key with the command.

Can you assign the PrintScreen key to a different command temporarily--something like opening the Home folder or the terminal? If that works, it's not your keyboard that's malfunctioning.

Also, can you try temporarily assigning another key combination to taking a screenshot (something like <Control><Shift>p) and seeing if that works? That way we can know if it's some special combination of PrintScreen and *gnome-screenshot*.

By the way, I made a keyboard shortcut for the command ```
gnome-screenshot --delay 5
``` and that pretty much takes care of the "taking a screenshot when I need to" bit.

---

### Post by ivar_m on 2006-06-17
I have the same problem. I first installed ubuntu and then added kde. Changing the key combination didnt help. I created an application that does the job, but it's not same.

---

### Post by Eddieduce on 2006-08-14
> **aysiu said:**
> 
By the way, I made a keyboard shortcut for the command ```
gnome-screenshot --delay 5
``` and that pretty much takes care of the "taking a screenshot when I need to" bit.[http://ubuntuforums.org/images/smilies/icon_surprised.gif](http://ubuntuforums.org/images/smilies/icon_surprised.gif)

[http://ubuntuforums.org/images/smilies/icon_arrow.gifHey](http://ubuntuforums.org/images/smilies/icon_arrow.gifHey), I'm new to Ubuntu & linux and wanted to know what type of file this would be saved as and how?

[http://ubuntuforums.org/images/smilies/icon_arrow.gifWhat](http://ubuntuforums.org/images/smilies/icon_arrow.gifWhat) is the application that runs to take a screen shot? and

[http://ubuntuforums.org/images/smilies/icon_arrow.gifDoes](http://ubuntuforums.org/images/smilies/icon_arrow.gifDoes) it already come integrated with ubuntu?

---

### Post by aysiu on 2006-08-14
It saves as a PNG file and asks where you want to save it (it defaults to saving on your desktop). It uses the *gnome-screenshot* application. It already comes with a default Ubuntu installation.

---

### Post by Eddieduce on 2006-08-14
I meant, how did you save your script to your desktop?  or
how did you save your text doc. as a an executable?

---

### Post by aysiu on 2006-08-14
It's not a script. It's a keyboard shortcut.

I used method B as described here:
[http://doc.gwos.org/index.php/GnomeKeyboardShortcut](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

---

### Post by Eddieduce on 2006-08-14
Thaks for the iformation.  That answers my forum question.

---

### Post by marel791 on 2007-11-25
I'm new and I had the same problem but I set the print screen button to start the app "KSnapShot" which seems to make it work like it used to before it stopped working.

---

