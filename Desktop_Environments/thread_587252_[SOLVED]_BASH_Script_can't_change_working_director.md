---
title: "[SOLVED] BASH Script can't change working directory"
date: 2007-10-22
forum: Desktop Environments
---

### Post by tbrminsanity on 2007-10-22
I have a script I need to run through a crontab.  The script is as follows:
> 
#!/bin/bash
cd /home/tom/friends/
java -jar emailpopulator.jar -t


The script is suppose to goto the friends directory and run the emailpopulator.jar file.  It will run the file if I run the script in the friends folder but otherwise it gives me the following error:

> : No such file or directorycd: /home/tom/friends/

How do I force the current working directory to be /home/tom/friends/ ?

If that is not possible I need to find a way to run the emailpopulator.jar in that folder.  The crontab keeps wanting to run from /home/tom/ .

---

### Post by mannih2001 on 2007-10-25
To which user's crontab did you add the entry? Can you run the script from a terminal?

---

### Post by tbrminsanity on 2007-10-26
The script runs from the terminal.  I think I may have figured it out.  With crons you need to assume that you are always in the wrong directory and the computer knows $#!t.  You have to have the full path of everything.  I fixed the following script by having the following cron:

* * * * * /bin/bash emailpopulator.sh

---

