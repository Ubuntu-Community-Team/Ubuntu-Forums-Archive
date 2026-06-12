---
title: "Scripting a computer shutdown"
date: 2007-09-21
forum: Desktop Environments
---

### Post by davosmith on 2007-09-21
I've set up a script that uses a combination of my video capture card, the bash at command and mencoder to timer record TV programs.

It seems to work well, but I'm struggling to work out how to get it to shut the computer off once it's done (I most often want to record something so I can go to bed, but would rather the computer wasn't sitting there, eating electricity all night).

I have tried the 'shutdown -h now' command, but it complains that I need to be root to do this. I don't want to run the whole script as root as I want it to have access to my home folder as the place to save the videos. I also don't want to have to get up in the middle of the night to type in my password, as that would defeat the whole point of the exercise.

Anyone got any suggestions? (please let me know if this is the wrong place to post this)

---

### Post by inik on 2007-09-21
try 
sudo shutdown -h 0 
it's same but with root priv 
(maybe it's  needs to edit /etc/sudoers  file)

---

### Post by davosmith on 2007-09-21
'sudo shutdown -h now' will work, but only if I'm there to type my password. The use-case I'm looking at is having a tv program record until 1am and then run a shutdown without me being there.

---

### Post by vikram on 2007-09-21
one option is that you can run your script as a regular user and schedule a shutdown seperately as root. not the ideal solution as you have to estimate the time but i have found the at command usefull here [http://www.karakas-online.de/gnu-linux-tools-summary/scheduling.html](http://www.karakas-online.de/gnu-linux-tools-summary/scheduling.html)

also never tried to run a script as a particular uid as I have heard its not secure so havent tried it.

you can also try adding a time to shutdown ?

[http://unixhelp.ed.ac.uk/CGI/man-cgi?shutdown+8](http://unixhelp.ed.ac.uk/CGI/man-cgi?shutdown+8)

---

### Post by davosmith on 2007-09-22
Thanks for your replies.

I think that the best solution I've found so far is to just give up and use 'sudo at <starttime>' to schedule my recording script and then add a 'chown' and a 'chgrp' to my script to give myself ownership of the file (technically a security risk running a script as root, but only an issue if someone hacks into my system and knows to mess around with that particular script, on a day when I am recording something).

---

### Post by davosmith on 2008-02-28
Managed to come up with a better solution for myself the other day:

A script (stored in /usr/local/bin, only editable / runnable by root) which is run every 5 min by cron which:

1. looks for a file called '.please-shutdown' in my home directory
2. deletes the '.please-shutdown' file
3. schedules a shutdown for 2 min later (to give me time to cancel it if I want to).

So all my tv record script now needs to do is to create an empty file called '.please-shutdown' when it has finished the recording. No need for a user-editable script to be running with root privileges.

---

### Post by [z]er0 HP on 2008-02-28
you could run the first script and when you want it to shutdown tell it to run a second script which runs as root

---

### Post by davosmith on 2008-02-29
But how can I run the second script as root, when the first script is not running as root (short of using 'sudo' and having a message pop up asking for my password (at 2am when the tv program I was recording has finished)).

---

