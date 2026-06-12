---
title: "Moving/copying/pasting a file from the desktop to a folder question"
date: 2022-05-02
forum: Desktop Environments
---

### Post by jmichaels29 on 2022-05-02
***Moving/copying/pasting a file from the desktop to a folder question - using 20.04 lts***

Many moons ago, I complained about the inabilities of being able to use the GUI to simply drag and drop a file/folder from a folder to the desktop and back then I decided to stick with Unity as my desktop environment.  Since then, I've discovered I can use the "move to" or "copy to" options via right clicking the file folder.  This is also why I'm excited about moving to Ubuntu 22.04 lts, as such drag and drops, via mouse, are now possible (fixed in the later versions of Gnome I do believe).  However, after trying to upgrade to 22.04 lts via the terminal resulted in an unrecoverable system crash (unrecoverable to me) [that I recently posted about also].  Instead of dong a fresh install of 22.04 lts, I've decided to wait (until August I believe) for Ubuntu to allow me to upgrade to it.  

Waiting is no problem.  But I recently have some files on my desktop, that I've been unable to "move to" or even "copy" and later paste to a desired folder, in "home."  I don't get the option to "move to."  I can "copy" but then later when navigating to a folder, there is no "paste" option available upon right clicking while in the folder.

What's the solution?

 
Regards,

jmichaels

---

### Post by TheFu on 2022-05-02
Do it from a shell/CLI using bash.

Most of the time, files on the desktop are in this crazy directory in the user's HOME directory called .... er .... "~/Desktop/".  So you can move/copy any files in that directory to a place you want them.
Of course, if the system is setup for a different language, the name "Desktop" would be in the local language.

---

### Post by ajgreeny on 2022-05-02
Were you trying to upgrade from Ubuntu 20.04 Unity to Ubuntu 22.04 with the gnome default DE?

If so that could be why you had an unrecoverable system crash.
Ubuntu with the Unity desktop is not upgradable to the default gnome desktop of the standard Ubuntu system.

As for copying or moving files in gnome, apart from using command line which is much easier and quicker than opening a file manager, I can not help you as when I had my first look and use of gnome, it immediately told me it was not for me; nothing in the gnome GUI makes much sense to me.

---

### Post by him610 on 2022-05-03
@ajgreeny
> nothing in the gnome GUI makes much sense to me.

++100% agree

---

### Post by jmichaels29 on 2022-05-03
> **TheFu said:**
> Do it from a shell/CLI using bash.

Most of the time, files on the desktop are in this crazy directory in the user's HOME directory called .... er .... "~/Desktop/".  So you can move/copy any files in that directory to a place you want them.
Of course, if the system is setup for a different language, the name "Desktop" would be in the local language.

I'm too novice to move the files/folders using "shell/CLI using bash."

I will try to use the GUI to find /Desktop/ in the HOME directory and try moving them around with the mouse.

I'm actually seriously considering installing Ubuntu 22.04 lts with a clean install on my desktop.  Not on my laptop though, cuase I have too many problems getting my broadcom wireless to work with it after a clean install - I'll wait until August to do an update on the laptop...

---

### Post by jmichaels29 on 2022-05-03
> **ajgreeny said:**
> Were you trying to upgrade from Ubuntu 20.04 Unity to Ubuntu 22.04 with the gnome default DE?

If so that could be why you had an unrecoverable system crash.
Ubuntu with the Unity desktop is not upgradable to the default gnome desktop of the standard Ubuntu system.

As for copying or moving files in gnome, apart from using command line which is much easier and quicker than opening a file manager, I can not help you as when I had my first look and use of gnome, it immediately told me it was not for me; nothing in the gnome GUI makes much sense to me.

I was attempting to install 22.04 lts on the day in April when it was officially suppose to be released - I use the command line in terminal to attempt it.  It went through the entire install process and even asked me to restart at the end.  Resulted in an unrecoverable system crash...

---

### Post by TheFu on 2022-05-03
> **jmichaels29 said:**
> I was attempting to install 22.04 lts on the day in April when it was officially suppose to be released - I use the command line in terminal to attempt it.  It went through the entire install process and even asked me to restart at the end.  Resulted in an unrecoverable system crash...

This report isn't enough details for anyone to help. Sorry.

BTW, /Desktop/ doesn't exist.  ~/Desktop/ is the same as $HOME/Desktop/.   Leading / characters in a path mean something very specific and missing saying "Desktop" isn't actually clear to say which directory you mean - not technically - but people will assume you mean ~/Desktop/ and that your PWD is $HOME.

Understanding relative and absolute directories is 100% the same in Windows and Linux, but if you've never used cmd.exe or command.com or any other shell, then you've probably never been forced to learn this.  A directory with a starting / in Unix is like saying C:\.  

One more thing that might blow your mind - MS-Windows doesn't actually have to use the \ to separate directories.  A / works perfectly, everywhere too.

---

### Post by jmichaels29 on 2022-05-03
Well, it can't be easily done in 20.x lts, but is easily done in 22.04 lts....

---

