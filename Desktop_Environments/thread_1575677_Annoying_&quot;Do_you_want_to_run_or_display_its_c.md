---
title: "Annoying &quot;Do you want to run or display its content?&quot;"
date: 2010-09-16
forum: Desktop Environments
---

### Post by mr_teatime on 2010-09-16
I'm working with .conf files which I need to edit (with gedit for example) and an .sh file which I need to run occasionally.
And every time I open a .conf file it pops the "Do you want to run or display its content?" question.
I tried to configure Nautilus to stop prompting me every time by setting the Edit->Preferences->Behavior to Run executable text files when they are opened.
But now every time I try to run the .sh file it opens it in gedit instead of running it.
Is there anyway to set the behavior for specific file types?
Like so it'd open the .conf files in a text editor and run the .sh files?

(Maybe I should mention that I'm running Ubuntu 10.04 with Gnome)

---

### Post by sourchier on 2010-09-16
Why don't you try to right-click the the file. Then Options --> then select Open With. Is there something else you are trying to do?

---

### Post by mr_teatime on 2010-09-16
Obviously the open with is set to gedit for the .conf files but it still pops the prompt every time I try to open the files.

---

### Post by ad_267 on 2010-09-16
I'd create .desktop launchers for the .sh files and then set nautilus to edit executable files.

Edit: Actually, why are the .conf files executable? They shouldn't have to be.

---

### Post by mr_teatime on 2010-09-16
> **ad_267 said:**
> 
Edit: Actually, why are the .conf files executable? They shouldn't have to be.

I was wondering the same thing.
Do you know where I can change it so they won't be executables?

---

### Post by ad_267 on 2010-09-16
The "exacutability" is a property of each individual file so you'll have to select them all and right click, then go to file properties, permissions and unmark the executable property.

---

