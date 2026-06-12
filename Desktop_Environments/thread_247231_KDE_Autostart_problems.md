---
title: "KDE Autostart problems"
date: 2006-08-30
forum: Desktop Environments
---

### Post by adverseyaw on 2006-08-30
Hi all.
I am having a problem trying to run a shell script at the start of a session.  I have put a script into the ~/.kde/Autostart folder that is supposed to execute at the start of my KDE session.  But instead of executing it opens in Kate.
Here is the script...
```

 #!/bin/sh 
 /usr/local/bin/fsfn -o

```
this is to enable the extra keys on my Sony laptop, with an overlay for Volume and Brightness.  The keys work without it, however I get no overlay.

1.  Is this problem because I am already running fsfn as a service?
2.  Is this because I have the default action to open a script and not run it?  (if so where do I change that?)
3.  Is there another place where I am already running fsfn the service and not the script?

Thanks,
adverseyaw

---

### Post by jimbren on 2006-08-30
If it is opening in a text editor, my guess would be that it is not executable yet.  Is it?

---

### Post by adverseyaw on 2006-08-30
Yes, it is.  I thought that also so I checked it, and it was green in ls but just to be sure I did chmod +x fsfn and restarted the Xwin (CTRL-ALT-Backspace).  When KDE came up again it still opened in Kate.

---

### Post by adverseyaw on 2006-09-01
Ok, for all who were watching this thread because they had the same problem. Here is the solution...
if you use a shell script in ~/.kde/Autostart/ it must have the shell *.sh extension to be run and not opened in Kate.
AdverseYaw

---

### Post by Ruskie on 2006-10-25
Uh... Slightly different issue here... Instead of putting a script, I created a softlink like this:

ln -s /usr/bin/gmail-notify gmail

Are there any counterindications in doing that???

---

### Post by kerry_s on 2006-10-25
> Uh... Slightly different issue here... Instead of putting a script, I created a softlink like this:
 
 ln -s /usr/bin/gmail-notify gmail
 
 Are there any counterindications in doing that???

Nope should be fine as long as it works. 

> Hi all.
 I am having a problem trying to run a shell script at the start of a session. I have put a script into the ~/.kde/Autostart folder that is supposed to execute at the start of my KDE session. But instead of executing it opens in Kate.
 Here is the script...
 
Code:
 #!/bin/sh 
 /usr/local/bin/fsfn -o
this is to enable the extra keys on my Sony laptop, with an overlay for Volume and Brightness. The keys work without it, however I get no overlay.
 
 1. Is this problem because I am already running fsfn as a service?
 2. Is this because I have the default action to open a script and not run it? (if so where do I change that?)
 3. Is there another place where I am already running fsfn the service and not the script?
 
 Thanks,
 adverseyaw

You forgot to put "&" at the end. Also there needs to be a new line after.
The "&" is so it doesn't have to wait on the script to continue loading the desktop.
I also use a script to start my apps.->

---

### Post by Ruskie on 2006-10-26
Thanks!

---

