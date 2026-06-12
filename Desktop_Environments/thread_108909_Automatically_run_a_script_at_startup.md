---
title: "Automatically run a script at startup"
date: 2005-12-27
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-27
To connect to the internet I need to run a script.

I want to connect automatically when I startup my machine.

How do I do that?

Gabriel

---

### Post by xmastree on 2005-12-27
Try putting the script in /etc/init.d/

---

### Post by fdimmling on 2005-12-27
[QUOTE=xmastree]Try putting the script in /etc/init.d/[/QUOTE]

This will not make the script to be run. You must have a link to this script in the directory belonging to the runlevel where it should be run, e.g. rc2.d for the default runlevel 2. The link must have a name like S23myscript, where S means Start Service myscript and the number 23 gives the position in the sequence of starting the services. You should study some examples there to understand the init process or read some tutorial.

Friedrich

---

### Post by xmastree on 2005-12-27
[QUOTE=fdimmling]This will not make the script to be run. You must have a link to this script in the directory belonging to the runlevel where it should be run, e.g. rc2.d for the default runlevel 2.[/QUOTE]
That's the best thing about these forums, you learn something every day. :) 

I didn't know that, thanks.

And I apologise for giving out incorrect advice in my post. :???:

---

### Post by Lambert on 2005-12-27
to make the link proper use this command command

Put the script in /etc/init.d/ making sure it has proper permissions.

then

```
sudo update-rc.d <script> start 50 2 .
``` 
replace <script> with the name of the file in /init.d/ (you don't need full path, just script name as command looks in that file automatically and matches name to file)

start makes it a start up link.

50 is the position in the start up sequence. You may have to play with this number so it starts at the right spot. You'll have to remove the first link you make though with sudo update-rc.d -f <script> remove then rerun the start command changing the the number.

2 equals the runlevel it puts the link in you can change this if you don't use the default ubuntu runlevel. You can also put it in all runlevels by putting spaces in between start 50 1 2 3 4 5 6 .

make sure there is a space and . at the end of the command

you can read man update-rc.d for more information

---

### Post by ACK!! on 2005-12-27
[QUOTE=Lambert]to make the link proper use this command command

Put the script in /etc/init.d/ making sure it has proper permissions.

then

```
sudo update-rc.d <script> start 50 2 .
``` 
replace <script> with the name of the file in /init.d/ (you don't need full path, just script name as command looks in that file automatically and matches name to file)

....[/QUOTE]


This is the best approach imho.  Often you get in any computer forum multiple ways to do the same thing and that is ok.  All the above suggestions will work but the one I just quoted is probably the very best cleanest way to accomplish the task.

---

### Post by GabrielWolff on 2005-12-27
I don't have permission to copy the file into that folder. How come?

G
OK, ignore this, I got it working through the console

---

### Post by GabrielWolff on 2006-01-03
I placed the script where it should be, and indeed the machine tries to connect at startup, but then there's an error message:
Unable to authenticate PAP.

What?

G

---

### Post by rajan on 2006-03-05
good call Lambert. i needed to start a program at startup so that it runs in the background and i'm too lazy to click on an icon. i made the changes recommended here and now the system works well and as ACK said, the fix is very clean.

incidentally the program was BOINC and if anyone is looking to run it automatically, use this informal "howto" above.

---

