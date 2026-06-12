---
title: "Bash navigation in gnome-terminal"
date: 2005-02-11
forum: Desktop Environments
---

### Post by piedamaro on 2005-02-11
I'd like to have <ctrl>left <ctrl>right  to jump at the beginnig and at the end of words in gnome-terminal. It would be nice to have pagup and pagdown to jump at the beginning and at the end of bash history too. The ultime goal for me is to have the linux console to behave the same (i.e. <alt-gr>^ yields ~ etc.) :)
Does anyone have any hints?

---

### Post by piedamaro on 2005-02-14
Cmon, no keyboard gurus out there? I can't believe it :)

---

### Post by mendicant on 2005-02-14
You can check the bash man pages for this kind of information.  Look for the line ''READLINE".  Basically, you'll need to modify ~/.inputrc to have the key strokes you want and the commands corresponding to those key strokes.  Alternatively, just use the existing key bindings (both emacs and vi style bindings exist).

---

### Post by piedamaro on 2005-02-14
Big thanks! This is what I was looking for. I'll try to set up my .inputrc and let you know. :)
(I know about emacs/vi keybindings, but it's awkward to use C-? when you can use arrows.)

---

### Post by mendicant on 2005-02-14
That's funny--I find it awkward to use the arrows when I can keep all my fingers around the home rows :)  To each their own, I suppose.  

BTW, to check what the arrow keys produce, do something like <Ctrl>-v <left arrow>.  You can also check out /usr/share/doc/bash/inputrc.arrows

---

### Post by piedamaro on 2005-02-14
You're totally right, the fact is that probably you're more advanced than me at typing, and I suppose you do touch-typing, while I do a sort of...:) Also I never learned bash shortcuts completely, I just use the more obvious ones: C-u, C-y, C-c, C-d. but to move cursor, I like it to be the same as in a text editor.
Oh, and your inputrc advice saved me a lot of time on google, all I needed to do was to uncomment few lines in /etc/inputrc, thanks! :D

---

### Post by thegreedyturtle on 2008-03-04
Ctrl + A     Go to the beginning of the line you are currently typing on
Ctrl + E     Go to the end of the line you are currently typing on
Ctrl + L                   Clears the Screen, similar to the clear command
Ctrl + U     Clears the line before the cursor position. If you are at the end of the line, clears the entire line.
Ctrl + H     Same as backspace
Ctrl + R     Let's you search through previously used commands
Ctrl + C     Kill whatever you are running
Ctrl + D     Exit the current shell
Ctrl + Z     Puts whatever you are running into a suspended background process. fg restores it.
Ctrl + W     Delete the word before the cursor
Ctrl + K     Clear the line after the cursor
Ctrl + T     Swap the last two characters before the cursor
Esc + T     Swap the last two words before the cursor
Alt + F     Move cursor forward one word on the current line
Alt + B     Move cursor backward one word on the current line
Tab     Auto-complete files and folder names

From [http://www.hypexr.org/bash_tutorial.php#multiple](http://www.hypexr.org/bash_tutorial.php#multiple)

So you want Ctrl + A and Ctrl + E

---

