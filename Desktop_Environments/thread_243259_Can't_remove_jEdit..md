---
title: "Can't remove jEdit."
date: 2006-08-24
forum: Desktop Environments
---

### Post by neko18 on 2006-08-24
**I solved the problem now, if anyone else has troubles with this, you can see my solution at post #12 of this thread here: [http://www.ubuntuforums.org/showpost.php?p=1418872&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1418872&postcount=12)**


Original post follows...
--------------------------------

I grabbed myself a copy of jEdit from here [http://www.jedit.org/index.php?page=download](http://www.jedit.org/index.php?page=download) and installed it with GDebi and it came up with an error. Now I can't remove it.

Here's some info on the matter, if it helps:
```
rick@rick-laptop:~/Desktop$ sudo dpkg -r jedit
(Reading database ... 108476 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit
rick@rick-laptop:~/Desktop$
```

```
rick@rick-laptop:~/Desktop$ sudo apt-get remove jedit
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  jedit
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 21.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108476 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit
E: Sub-process /usr/bin/dpkg returned an error code (1)
rick@rick-laptop:~/Desktop$
```

Would it somehow be possible to remove jEdit from the APT database then remove the files by hand?

---

### Post by neko18 on 2006-08-24
Anyone? Please?

---

### Post by peabody on 2006-08-24
> **neko18 said:**
> Anyone? Please?

I believe there was another thread somewhere with the exact same subject, let me see if I can find it.

---

### Post by neko18 on 2006-08-24
Ok, thanks.

---

### Post by peabody on 2006-08-24
[http://www.ubuntuforums.org/showthread.php?t=232270&highlight=jEdit](http://www.ubuntuforums.org/showthread.php?t=232270&highlight=jEdit)

That seemed to be the same problem?

---

### Post by neko18 on 2006-08-24
Thanks a ton! I'll try that out.

---

### Post by neko18 on 2006-08-24
I tried 
```
sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
```
with no luck.

Here's the output:
```
rick@rick-laptop:/var/backups$ sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
(Reading database ... 108476 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit
rick@rick-laptop:/var/backups$ 
```

---

### Post by peabody on 2006-08-24
> **neko18 said:**
> I tried 
```
sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
```
with no luck.

What exactly did it say or do?  "with no luck" isn't very descriptive.

---

### Post by cstudent on 2006-08-24
What was the original error message when you tried to install jedit? If you tried to install with Gdebi, then you probably don't actually have any proble m. So far, my experiences with Gdebi have been good with packages that didn't have met dependencies.

If you want jedit, try following the advice in the other thread on adding the repositories to your souces.list and try to install jedit again.

---

### Post by neko18 on 2006-08-24
@peabody: You must've seen my non-edited post, sorry. I added the output now.
@cstudent: I'll try the sources.list thing.

---

### Post by neko18 on 2006-08-24
Adding the jedit lines to my sources.list and running this didn't work:
```
rick@rick-laptop:/var/backups$ sudo apt-get update && sudo apt-get upgrade
[clip]
Fetched 5B in 7s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  jedit
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 21.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108476 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit
E: Sub-process /usr/bin/dpkg returned an error code (1)
rick@rick-laptop:/var/backups$

```

---

### Post by neko18 on 2006-08-24
**Edited on 2007-06-19. Huge typo!**
-------------------

**Solved!**

Thanks for the help everyone. Here's what I did to slay the beast:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.jedit.bak
sudo kate /var/lib/dpkg/status
```
Now I hit Control-F and searched for the string "jedit" and removed this block:
```
Package: jedit
Status: deinstall ok half-installed
Priority: optional
Section: contrib/editors
Installed-Size: 20533
Maintainer: Slava Pestov and others <devel@jEdit.org>
Architecture: all
Version: 4:04.03.06.00
Replaces: jedit-cvs
Conflicts: jedit-cvs
Description: A real editor for programmers
 As one of the most feature rich editors available, jEdit boasts
 support for syntax highlighting in more than 140 languages. jEdit
 is more  than just an editor, and its functionality is extended by
 the use of 'plugins' which include tools for ant and console
 integration as well as a host of other features. Any serious
 programmer will undoubtedly want to give jEdit a good look.
 .
 More information about jEdit, its plugins, macros, etc. can be
 found at http://www.jEdit.org/.
```
Then I closed Kate and ran:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.jedit.bak
sudo kate /etc/apt/sources.list
```
And removed the two jEdit lines I had added earlier, then closed Kate. After that I ran:
```
sudo apt-get update
```
Then to make sure there were no problems I ran:
```
sudo apt-get upgrade
```


Thanks for the help everyone!

---

### Post by cstudent on 2006-08-24
Good for you. :)

And thanks for posting your solution. I'm sure it will come in handy again someday.

---

### Post by topgan1 on 2006-09-01
im having the same problem and i did 
```

topgan1@teh:~$ sudo cp /usr/lib/dpkg/status /usr/lib/dpkg/status.jedit.bak 

cp: cannot stat `/usr/lib/dpkg/status': No such file or directory

```

I also tried 
```

topgan1@teh:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 96623 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit

```

So no /usr/lib/dpkg/status file to edit. What's wrong? help plx :D](*,) ](*,)


**EDIT:**
I finally solved the problem after 30seconds i did this post :)
I had to remove all /var/lib/dpkg/info/jedit.* files. Then the "topgan1@teh:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq jedit" command worked smoothly and did the job. Now I can use the repositories again.

---

### Post by ounas on 2006-09-17
> **topgan1 said:**
> im having the same problem and i did 
```

topgan1@teh:~$ sudo cp /usr/lib/dpkg/status /usr/lib/dpkg/status.jedit.bak 

cp: cannot stat `/usr/lib/dpkg/status': No such file or directory

```

I also tried 
```

topgan1@teh:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 96623 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit

```

So no /usr/lib/dpkg/status file to edit. What's wrong? help plx :D](*,) ](*,)


**EDIT:**
I finally solved the problem after 30seconds i did this post :)
I had to remove all /var/lib/dpkg/info/jedit.* files. Then the "topgan1@teh:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq jedit" command worked smoothly and did the job. Now I can use the repositories again.



Thanks that worked for me..

:p

---

