---
title: "Gnome idea: delete trash that is over x days old."
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by eladamri on 2007-04-05
Hello all,

This is a feature that I have been looking and waiting for for quite some time. The trash in Gnome needs a feature that will automatically delete files that are older than x days. 30 seems a reasonable choice for x.

The concept seems to be so obvious that I don't know why it hasn't been implemented or at least have more complaints that no such feature exists. I am most frustrated because I think I remember Windows having this feature. *There is no reason in the world that an Ubuntu user should have to be jealous of a Windows feature!*

The motivation is simple. We're all busy, who wants to deal with cleaning up your trash bin? Also, if you don't retrieve something from it in 30 days, then you probably never will.

As far as a solution goes, would a Nautilus script be best? I'm not a programmer so I can't say.

If you have a suggestion or can point me somewhere else for direction please let me know. There has to be a simple way to implement this in Gnome for a beginning user.

---

### Post by eladamri on 2007-04-05
Oh yeah. If this thread is in the wrong place can someone move it to a new, more fitting place?

---

### Post by aanderse on 2007-04-05
schedule the command rm -rf ~.Trash for every 30 days and you'll have what you want.

---

### Post by eladamri on 2007-04-05
Thank you for your reply, but this would delete everything in the trash whereas my goal is to delete only the files and folders in the trash that are *more than* thirty days old.

Also, the Gnome trash will look for trash folders that are in nfs folders, mounted discs like USB drives and the like that a script using '~.Trash' will not find.

---

### Post by reclusivemonkey on 2007-04-06
> **eladamri said:**
> Thank you for your reply, but this would delete everything in the trash whereas my goal is to delete only the files and folders in the trash that are *more than* thirty days old.

Also, the Gnome trash will look for trash folders that are in nfs folders, mounted discs like USB drives and the like that a script using '~.Trash' will not find.

You can execute a command from the results of find using the '-exec' flag. That's where I would start to produce this sort of script. 

```

man find

```

Will tell you all you need to know.

---

### Post by aanderse on 2007-04-06
ah sorry i didn't differentiate between deleting the trash bin every thirty days and deleting files that were thirty days old.

this is still very possible though, you can just write a small bash script that includes all the directories you want it to search then, as reclusivemonkey pointed out, use find with the date being such that the file is greater than thirty days in the target directories and execute the rm -f command.  have your system schedule that once a day and you'll have exactly what you want :-)

---

### Post by altaaa on 2007-04-06
This is actually a bit harder than it seems.

When you delete a file, it's moved to the Trash. But it keeps the original date information, so if you would write a script that deletes every file older than 30 days, it does *exactly that*.

Example:
You have had a file named 'test' for about 100 days on your filesystem. If you delete that file today and then run the script, it will be deleted, because the date doesn't change. In other words, the file 'test' is older than 30 days, but it only has been in your Trash for seconds/minutes.

You would somehow have to touch every file when it is put in one of the various .Trash directories.

---

### Post by aanderse on 2007-04-07
yeah good point, i guess modifying the "Move to Trash" command and adding a "touch" command to that script would be one way of doing it.  this is getting a bit involved for just a "quick fix" though ... so maybe this could be turned into an actual project.  or someone else has a quick fix.  was just trying to be helpful, sorry no solution yet.

---

### Post by eladamri on 2007-04-12
Thank you. I have had a bash script written up for some time, but it fell short for the reason that was pointed out.

There must be a solution that can be integrated into the Gnome/Nautilus trash system easily. It seems that a bash script is not the solution.

---

### Post by reclusivemonkey on 2007-04-12
Personally, I think any kind of automated delete is a *very* bad idea. However, you can request features via launchpad.

---

### Post by eladamri on 2007-04-12
That's just the thing. Since there is no automated trash emptying feature I check my trash every so often and empty it. Only, since there are so many files in it I cannot check every one too scrutinously to see if I may still need it.

However, if I do need to retrieve an item from the trash I will definitely do so within 30 days. So implementing such a feature would be safer. At least in my case.

I have not heard of Launchpad, but it sounds like that's where I'm headed. Thank you.

---

### Post by brownslink on 2008-04-22
It seems that computers should implement tedious, repetitive tasks for us, as long as we have complete control.  The algorithm I would choose is the following.

X # minimum free space desired
Y # minimum age desired
W = false # Is a warning required to the user?
T = trash() # trash file list sorted by age ascending

# While free space is too low and the trash exists:
while( ( trash_free_space() < X) && ( length( T) > 0):
[INDENT]# Fetch the oldest file removing it from the list.
   F = pop( T) 
   # Is it too young?
   if( age( F) < Y):
[INDENT]# (yes) Remember to warn the user.
      W = true
[/INDENT]# Delete the file.
   delete( F)
[/INDENT]# Does the user need a warning?
if( W):
[INDENT]# Generate the warning.
   warn_user()
[/INDENT]I'm sorry but I think in code first and then generate the text.

---

