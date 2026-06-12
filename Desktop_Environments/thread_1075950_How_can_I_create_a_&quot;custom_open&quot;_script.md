---
title: "How can I create a &quot;custom open&quot; script?"
date: 2009-02-20
forum: Desktop Environments
---

### Post by lariosa42 on 2009-02-20
Hello all.  I often find myself opening a whole bunch of windows for a certain task, and then moving them all around to the positions I like.  For example, I might want to write a program in gedit and compile it in the terminal while reading a pdf file.  I like to be able to see everything at once.  Thus, every time I sit down to do this, I have to open a terminal window, move it and resize it, open gedit, move and resize, and open the pdf, move and resize.  Needless to say, this gets a little tiresome.

My solution is to write a shell script that opens all the windows to the right sizes and positions (I'm using Gnome).  So far, I can do this with the terminal, but not with other programs.  I am new to shell scripting, but here is my attempt so far:

```

#!/bin/bash
gnome-open ~/Desktop/ProjectX/program.f ;
gnome-terminal --geometry 74x9+0+600 ;
gnome-open ~/Desktop/Manuels/Programming_Basics.pdf

```

It works OK, but I can't seem to get --geometry tags to work with gnome-open.  Also, it would be nice if I could get the terminal to open in a specific directory.  Another thing that would be great is if I could open programs to a few different workspaces.  I look around online for a few hours, but didn't find much.  Any tips or other ideas?

Thanks! =)

---

### Post by Blackdragon1400 on 2009-02-20
ive got a post up for much of the same problem, someone suggested that I try using wmctrl. u can try that but I had no luck. I have a question for you though, do you know how to add to the script to run commands in the terminal that you open with the new dimensions?

there is acctually an -x entry for gnome-terminal that lets you exucute commands within the first line, But I am not sure how to extend that into more than one command.

---

### Post by lariosa42 on 2009-02-21
Thanks for the reply.  It's good to know I'm not the only one stuck on this.  Unfortunately, I don't know how to pass commands to a particular terminal using a script (thanks for the -x tip though).

In general, I would like to know how to pass commands to programs from a script in general.  That is, it would be great if I could write a script that would, for example, open the editor "Kile," open my three most recent projects within Kile, compile them all, open the resulting dvi files (in the window positions I like), and finally return my cursor to the bottom of one of the files so I can just start writing.  Currently, I have to do this manually every time I start up my computer (which is a lot, since it is a laptop).

I don't know if all this is possible, but a man can dream can't he?

---

### Post by zhocchao on 2009-02-21
wmctrl does not work with compiz. Without compiz, you can use it to do what you want.
With devilspie you can also make rules for window positions (I think)

---

