---
title: "KDM hickup"
date: 2010-11-29
forum: Desktop Environments
---

### Post by Hakimjo on 2010-11-29
I have a nice stable Kubuntu 10.10 64 - until yesterday.

I did change some things in the startup system preferences.  Just playing really, also defining a personal image for the start-up screen.

Then I worked for while with Inkscape which on launch would give me a "internal error, will quit now".  Don't know whether this is related at all.  But it made me restart the computer and this is when the problem began.  Actually, it already had a kick-up on shut down, hanging at the "checking battery" ...

Then, on start-up it will not go beyond runlevel 3 (?), i.e. the shell prompt, where I can log in with my name and password, but no GUI.

I also tried the rescue mode and did "kdm" as root.  This launches the KDM routine for some seconds, but then falls back into shell.  When I try again, it does nothing at all.  When I do "init 5", it only brings me back to my own login in script.

The I looked at KDM help, and there is an option to run KDM with a backup preference file.  This might be the solution, since I suspect that a corrupted or badly tampered preferences file is the source of the problem.

But I am not so familiar with these things.  So, can somebody give me instruction on where to get that alternative file and how to use it from the shell ?

Thanks !

Joachim

---

