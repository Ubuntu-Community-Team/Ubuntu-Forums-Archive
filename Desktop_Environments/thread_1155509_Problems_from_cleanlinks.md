---
title: "Problems from cleanlinks"
date: 2009-05-10
forum: Desktop Environments
---

### Post by JonWasHere42 on 2009-05-10
This post is in reply to a previous similar post 
[http://ubuntuforums.org/showthread.php?t=695655](http://ubuntuforums.org/showthread.php?t=695655)

I was in the process of cleaning up my /usr/lib folder
and ran a cleanlinks to clean up dangling links. 
After this I tried to use gcc
and received the error:
```
cpp: error trying to exec 'cc1': execvp: No such file or directory
```

After searching around, the only suggestions I found was to (a) reinstall the OS (last resort), or (b) reinstall cpp.
Reinstalling cpp was problematic and I kept getting this error:

```
$ sudo dpkg --configure -a
dpkg: error processing cpp (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 cpp

```

From here I tried to apt-get install cpp, or dpkg -i cpp
only to receive an error like this:

```
debconf: Perl may be unconfigured (Can't locate IO/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
...

Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.

...

```

At this point the suggestions where to reinstall perl or the OS.
But before you do this, try a 
```
$ locate POSIX.pm
/usr/lib/perl/5.8.8/POSIX.pm

```

Note that this variable @INC contains '/usr/lib/perl/5.8', but not '/usr/lib/perl/5.8.8' 
So my solution (crude as it may be) I just created a symlink:
```
$ln -s /usr/lib/perl/5.8.8 /usr/lib/perl/5.8 
```

This fixed everything. I am sure there is a better way to do this, like to change whatever path variable @INC is, but I dont know how to do that.
Anyway, before you go and reinstall your OS or spend a weekend messing up all of your installed packages (like I did), give this a try. 

I hope this helps.

---

