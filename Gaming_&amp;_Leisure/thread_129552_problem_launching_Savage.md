---
title: "problem launching Savage"
date: 2006-02-14
forum: Gaming &amp; Leisure
---

### Post by Dillinger on 2006-02-14
I have installed and patched Savage but I'm having some problems launching it.  I get the following error message then the loading screen crashes after 3 or 4 seconds.

```

tyler@ubuntu:~$ /home/tyler/games/Savage/savage

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers
System_Init()
Game error during initialization:

Main GUI Error: Couldn't find scrollbuffer buddy_messages

```

The following is my locale output:

```

LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

Not really sure what the problem is google wasn't much of a help, any ideas?

---

### Post by zo0o0ot on 2006-09-05
I have the same problem.  I'm running kubuntu.

here is my error message.

```
woo@trogdor:~/games/Savage$ ./savage

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers
System_Init()

```

---

### Post by Casey on 2006-09-05
Hmm, I wonder if it's SEP/EX2 related.  Which one did you install (and which version)?

---

### Post by zo0o0ot on 2006-09-07
I installed both.
Per this site:
[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2511&post_id=12025#forumpost12025]("http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2511&post_id=12025#forumpost12025")
 I downloaded the files listed and went to this website:
[http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=55]("http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=55")
 and downloaded both additions that were on their site.  I may have incorrectly applied the patches, as I was unable to find any README or documentation on how to add the patches.  I just uncompressed the file, and pasted everything over from the compressed file into the savage directory, attempting to put everything in its respective space.  I did it in konqueror, not in the CLI, as I can never remember the easy command to do it for you.

Another point of interest:
I tried firing the game up again, and the game actually cuts out AFTER all of the text I indicated.  The game checks for updates, says "Your version of Savage is up to date", then starts to initialize.  The middle of the screen says "Intitializing", and the bottom right hand corner of the initialization screen says "Savage 2.00c" and after the black loading screen which indicates the silverback engine build date and savage version, it quits out without any further messages.
I'm also including a screenshot of the last thing before the init screen, as well as the init screen.  the little blue "Alt S" box on the init screen is from the screenshot program.

Any ideas?

---

### Post by zo0o0ot on 2006-09-08
FYI, I deleted the directory and installed it again.  The game works fine, but I haven't installed the SEP/EX2 mods yet (that is the likely culprit, I guess).  I'll keep you posted.

Edit: going back to the Evolved Savage Clan website shows a new SEP version, and highly suggests installing SEP instead of EX2, indicating that EX2 is not supported.

per the site under the EX2-5b download tab:
> 
WE RECOMMEND SEP OVER EX2 sine EX2 is no longer supported or in development within the savage community.

---

### Post by Casey on 2006-09-09
I'd suggest using the newest SEP version.  I have run that without problems.  EX2 used to be the primary enhancement but SEP has taken over where EX2 left off.

---

### Post by zo0o0ot on 2006-09-10
Yep, that did the trick.  Now, all I need to do is figure out how to play the game!

---

### Post by TigerWolf on 2006-09-18
I get the same problem with SEP. 

```

System_Init()
Game error during initialization:

Main GUI Error: Could not get scrollbuffer buddy_messages

```

Any ideas?

---

