---
title: "Help me. A question regarding Ubuntu bash command shell, Thanks~"
date: 2008-03-08
forum: Education &amp; Science
---

### Post by Xephyrind on 2008-03-08
hello,

I was trying to learn shell-command from software carpentry website: [http://swc.scipy.org/lec/shell01.html](http://swc.scipy.org/lec/shell01.html). It went smoothly upto This part:Creating Files and Directories. I did what the thing said and I used the command "edit venus.txt" I was wondering if anyone knows how to save changes in the editor? I am lost on the part that once after I got editing going with an --INSERT-- thing on the bottom, the gnome-terminal no longer takes my words as commands anymore. I don't even know how to save the file after that point, let alone leaving the file and going back to the tmp directory. In the end, I decided to simply shutdown gnome then call it again... however, I want to learn the correct method. Thank you~! Also I am not sure if I posted this in the correct forum... I thought this is rather closely related because I AM trying to learn shell-command to become a better program writer. I thought this is rather academically related so... Sorry if I've made the mistake.

---

### Post by Martje_001 on 2008-03-08
You can use nano as text editor on the command-line. CTRL-O to save, and CTRL+X to exit (for nano).

---

### Post by Xephyrind on 2008-03-08
Thanks for the help! uhmm. I am quite new to ubuntu. I was wondering  how to edit the file venus.txt through the terminal. In another word, how do I edit the file, save the file, quit the file, and go back to tmp directory after I've type "edit venus.txt" in command shell.

---

### Post by Martje_001 on 2008-03-08
Like I said, you can use nano. Use this command:
```
nano file.txt
```

---

### Post by Xephyrind on 2008-03-08
oh I c Thanks! I didn't know nano is a text editor built in already lol

---

### Post by oxsyn on 2008-03-09
VI is the classic editor.  A lot of people will swear by it.  It's got a pretty big learning curve though, but once you get the basics, it makes editing files in the CLI a breeze.

If you wanted to create a new file, you could type: vi mynewfile
As long as mynewfile didn't already exist, it would create it.  If mynewfile did already exist, you would begin editing it (as long as you have write permission).  If you don't have write permission, it would be opened in read-only mode.

VI uses two different modes: command mode & insertion mode.  When you enter VI, you'll be in command mode (you could use i, a, or A to enter insertion mode.  You get from insertion mode to command mode by pressing 'esc' ... sometimes more than once, lol).

In command mode:
x = delete current character
dd = delete current line
W = go forward one word
B = go back one word
R = replace current character with next typed character
i = enter insertion mode before cursor
a = enter insertion mode right after cursor
A = enter insertion mode at end of line
:w = write changes to file
:wq = write changes to file and quit

There are tons of things to learn in VI.  I'm still a VI noob, but the more I learn, the more I love it.

---

