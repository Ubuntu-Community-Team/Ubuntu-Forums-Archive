---
title: "[SOLVED] Home Folder Permissions"
date: 2009-01-10
forum: General Help
---

### Post by spongypants23 on 2009-01-10
Hi guys!

I recently went and fiddled with my home directory, recursively setting something that denied me access of all files. Whoops! Couldn't even log in.

Anyway, I managed to fix the situation by chmodding my entire home folder and all files in it to 774.

Is this ideal? If not, how to restore the home folder permissions back to default?


On a side note, Amarok is unable to find/start any sound engines now. Seems related since it started after the chmod to 774. Any fixes?

---

### Post by khelben1979 on 2009-01-10
I suggest you reinstall the amarok player.

When it comes to the file permissions on all the files in the /home directory, it all comes down to how you prioritize security and in this case you should be more cautious of how you use the chmod command on your files.

How you reset all the file's permissions to the default values I don't know, but I suggest that you read the man page for [the chmod command]("http://en.wikipedia.org/wiki/Chmod") so that you feel that you have more control of how the command works and what file permissions could be suitable for each file/catalog.

---

### Post by drs305 on 2009-01-10
> **spongypants23 said:**
> 
Is this ideal? If not, how to restore the home folder permissions back to default?

If you run into error messages on start regarding $HOME permissions or .dmrc not being set properly, refer to this thread:
[URL="http://ubuntuforums.org/showthread.php?p=6161267"]Solving .dmrc and $HOME Permission Errors
[/URL]

---

### Post by spongypants23 on 2009-01-10
@khelben1979

It's not that I don't know how chmod works. The reason I used 774 was because it was the only way I could get into my own home folder (644 and 664 didn't work). But I don't know if leaving every file executable is a good idea. (Although I know that I'm the only one who has those priveleges).

As for amarok, re-installing it didn't solve my problem.

It's not much a problem though, I removed it and got Banshee instead.

---

### Post by cdtech on 2009-01-10
I would use "755". All (or most) of my permission sets are at 755, excluding my .ssh directory which is set to 644.

---

### Post by spongypants23 on 2009-01-10
> **cdtech said:**
> I would use "755". All (or most) of my permission sets are at 755, excluding my .ssh directory which is set to 644.

Thanks for the advice :)

---

### Post by Hachi-Roku on 2009-11-27
interesting... sent me on a chmod lerning curve... awesome

---

