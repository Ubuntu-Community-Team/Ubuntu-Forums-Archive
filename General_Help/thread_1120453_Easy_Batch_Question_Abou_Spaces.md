---
title: "Easy Batch Question Abou Spaces"
date: 2009-04-09
forum: General Help
---

### Post by petersm2 on 2009-04-09
I'm new so this might be a dumb question.

I have setup gnome-schedule to do a backup of some folders using grsync but cron can't use the command "grsync" instead I have to use "grsync-batch".

Everything works fine, but here's the problem, if there is a space in the name of the folder that I'm trying to backup then the batch file gets hung up looking for only the first part of the folder name. For example, a folder named "Test1" works while a folder named "Test 1" doesn't.

Is there any way to fix this? Other than to rename all the folders I want to backup without spaces? Is there a way to edit the batch file to tell it to read spaces? Thanks.

---

### Post by mocoloco on 2009-04-09
FYI, they're not batch files, they're shell scripts.  Dos/Win batch files only run commands in a batch, while shell scripts are much more powerful and let you use real programming.

They app you'll want to look at using in gnome-schedule is rsync, which is the backend of what grsync uses. You'll find that Linux does a lot if this fronend backend stuff.
Open your help browser and search for rsync to read it's manual page, or open a terminal and type in "man rsync".

---

### Post by petersm2 on 2009-04-09
Thanks for the quick reply. I understand that rsync is what grysnc is using, but I'm very limited in using the command line. I'd much rather use a gui, unless absolutely necessary.

Are you saying there is no way to make the grsync-batch script able to read the spaces in my folder names? Because everything would work fine if this was possible. Thanks again.

Edit: I just typed the Rsync command, that is given when you run a Grsync session, into the terminal and found that rsync isn't able to read the spaces in my folder names either. I'm sure in the hours of searching for a solution on how to get cron jobs running that I've seen people using rsync with spaces in their folder names.

Is there somehting I'm missing here?

---

### Post by HermanAB on 2009-04-09
The secret is Quotation Marks.

Put quotes around the "filenames" or "variables" containing file names.  That will signal to the interpreter that the spaces are part of the string.

---

