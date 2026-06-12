---
title: "Evolution refuses to start"
date: 2008-09-13
forum: Desktop Environments
---

### Post by Cloggsy on 2008-09-13
Presenting symptoms: When attempting to open Evolution a message appears on the screen for a nanosecond advising me that Evolution has experienced an unexpected closure. Nothing further happens. Trying to "pounce" on the message to get it to either "Ignore" or "Recover" (the two options it seems to be offering) doesn't work. 

The data in Evolution seems to be intact. Clicking on the date on the top deskbar still allows me to see my appointments and tasks for most of my calendars in the drop-down (with the exception of the last calendar I was working on which doesn't now appear at all) but when I click on "Edit" I get either the same as above or the full Evolution calendar screen for a nanosecond before it closes. One particular appointment has decided that it is a permanent feature for every day.

What I was doing: I spent a lot of time yesterday entering four different calendars into Evolution - three personal for members of the family and one for the church as a business calendar. This latter one was the last one I was working on as I printed out a calendar for 2009 before closing the system down and this is the one which now does not appear on the drop-down.

What I have done:
a)Panicked
b)Deleted Evolution using Synaptic Package Manager and then reloaded using the other package manager. 

Still the same.

Help! (Please!)

---

### Post by Pro-reason on 2008-09-13
When you deleted Evolution, did you do a normal deletion or a full one (a purge, which removes configuration files too)?

To get more error messages to work with, run Evolution from the command line (type “evolution”).

---

### Post by Cloggsy on 2008-09-13
I suspect I may not have purged Evolution as I only ticked "removal" rather than "complete removal" on the synaptic. I was worried that "complete" removal" might have wiped all my data as well which I want to preserve. Also, being an Ubuntu virgin I just guessed the packages to remove and reinstall being those with "evolution" in the name. 

Tried the command line in Terminal and got:
$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...
Segmentation fault

---

### Post by Pro-reason on 2008-09-13
> **Cloggsy said:**
> I suspect I may not have purged Evolution as I only ticked "removal" rather than "complete removal" on the synaptic. I was worried that "complete" removal" might have wiped all my data as well which I want to preserve. Also, being an Ubuntu virgin I just guessed the packages to remove and reinstall being those with "evolution" in the name. 

Tried the command line in Terminal and got:
$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...
Segmentation fault

Doing a complete removal would indeed delete your personal configuration.  So, if you want to keep that, you did the right thing.

“Segmentation fault” is one of those annoyingly vague error messages.

Try moving your configuration files instead of deleting them:

```

mv ~/.evolution ~/.evolution.backup

sudo apt-get install --reinstall evolution evolution-common evolution-data-server evolution-data-server-dbg evolution-dbg evolution-plugins

evolution

```

Does it work now?  Do you at least get more informative error messages?

---

### Post by Cloggsy on 2008-09-15
Many thanks for your help - Pro-reason, sadly I think I've just uncovered something more sinister along the lines of a hardware fault as as the desktop isn't loading correctly and some of my Windows programmes are also crashing.:confused:

---

### Post by Cloggsy on 2008-09-15
It looks like I might need to replace my hard drive or similar and reload both Ubuntu & Windows from scratch. While I still have some functionality in Ubuntu is there a file I can save which will save my data so it can be accessed by a reloaded Evolution?

---

### Post by Pro-reason on 2008-09-15
> **Cloggsy said:**
> It looks like I might need to replace my hard drive or similar and reload both Ubuntu & Windows from scratch. While I still have some functionality in Ubuntu is there a file I can save which will save my data so it can be accessed by a reloaded Evolution?

It is perhaps best to backup your entire home directory.

But you could just back up ~/.evolution.

Do this command:

```
tar -cvjf ~/Desktop/Evolution-backup.tbz2 ~/.evolution

```
That will leave a backup file on your desktop for you.

---

