---
title: "Bash Script not calling Bash script"
date: 2009-01-07
forum: General Help
---

### Post by supradave on 2009-01-07
I have a fairly complicated back up script that appears to work.  But I have noticed recently that when calling another script from my backup script, it doesn't call the script (or if it does, it doesn't run).

Basically, my script starts:
#!/bin/bash

variables

more stuff for about 190 lines
then call my other script with

/bin/bash /dir/script.sh

---

The other script never gets called.  I have seen this happen in crontab jobs in particular.  I have markers that write to a file to know that the main script is running.  This used to work a couple weeks ago and I didn't change anything in the scripts.

Any ideas?

---

### Post by phisher1 on 2009-01-07
If you run the main script manually, not from cron, does the second script get executed?

And you shouldn't need to call the second script like you are calling it

/bin/bash /dir/script.sh

Simply

/dir/script.sh

---

### Post by supradave on 2009-01-07
Yes it does.  Should have specified that.

Perms are 775 for both scripts.

---

### Post by AlanMacdonald on 2009-01-07
Are there any exit statements in the script that could be running when you're not expecting it?  Potentially you could check the return status of the script if that is the case.

---

### Post by phisher1 on 2009-01-07
Also, you might try adding -x to your shebang to debug the script

---

