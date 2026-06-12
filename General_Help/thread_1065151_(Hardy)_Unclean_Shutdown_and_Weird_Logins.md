---
title: "(Hardy) Unclean Shutdown and Weird Logins"
date: 2009-02-09
forum: General Help
---

### Post by Vryko Lakas on 2009-02-09
So a wiggly power cable caused my computer to shut off and restart. This has happened before, and usually when it comes back on the error-checking utilities kick in and make sure everything's okay. Usually, they are. 

This time, the process failed at step 4/5 while checking the volumes, and I got a root commandline. 
I simply gave it the command to shutdown in a minute and restart. I went into the Recovery Mode from GRUB and let it run the automatic fixing utilities again, but it kept failing at 4/5. I repeated this process in the blind hope that something would start working. 
Sometimes, instead of restarting I would tell it to continue with the normal boot process and that got me to the Login screen. However, when I tried to log in with my password, I got the following error message: 
```
Your home directory is listed as: '/home/<username>', but it does not appear to exist. Do you want to log in with the /root directory as your home directory? It is unlikely anything will work unless you use a failsafe session.
```
I tried to log in with this, but it kicked me back out to the Login screen. 

I changed the Session setting to Failsafe, tried to log in as usual again, and was booted back to the Login screen where I simply pressed the Shutdown button. 
However, when it booted back up and went through the checking-failing song and dance again with no apparent difference, I entered ctrl+D at the root commandline, got to the login screen, logged in as another (non-Administrator) user, and *THAT* worked! Keeping this account logged in, I changed users and this time, *MY* account's login worked!

And here I am, logged in to a computer that I feel uncertain about, because *I never saw any errors get fixed*: things just magically kept working this time around. I'm afraid to turn the computer off, and I'm to make sure all our data is backed up to an external drive. 



So basically what I'm saying, I don't know what the problem is, or if was solved this final time. All I know is that somehow I'm logged in and everything seems normal from here. This is the family's computer, though, so I'd like to be certain it works without unintentionally breaking it. Is there something I can do to check and make sure things are still working as they should, rather than just assuming that they are because I managed to log in this time?

---

### Post by Vryko Lakas on 2009-02-11
Me again. 

Another power blink caused another unclean shutdown. Again, I can still get to the login screen and onward by pressing Ctrl+D, but only after it goes through a disk check and tells me it couldn't repair whatever was happening. 
However, this time I had the presence of mind to copy down what it was telling me before going on. 
It got about 93% through the check, and then returned:
```
/dev/sdb3: Unattached inode 6242368
fsck died with exit status 4
A log is being saved in /var/logs/fsck/checkfs if that location is writeable. Please repair the file system manually
*A maintenance shell will now be started. Control + D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

```
And then my root commandline. I used Ctrl+D, logged in, and checked in /var/ for the logfile. This is what I found: 
```
Log of fsck -C3 -R -A -a 
Wed Feb 11 14:31:45 2009

fsck 1.40.8 (13-Mar-2008)
/dev/sdb3 contains a file system with errors, check forced.
/dev/sdb3: Entry 'sessionstore.js' in /kyle/.mozilla/firefox/833g25ft.default (526835) has deleted/unused inode 527695.  CLEARED.
/dev/sdb3: Unattached inode 6242368


/dev/sdb3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Wed Feb 11 14:34:26 2009
```


Any help?

---

