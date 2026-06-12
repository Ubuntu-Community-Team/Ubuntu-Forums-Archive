---
title: "how do i make executables launch at login"
date: 2005-05-12
forum: Desktop Environments
---

### Post by tonysathre on 2005-05-12
each time i login my kstatus, kooldock and weather apps have to be relaunced ...how do i make them auto launch when i login

---

### Post by bored2k on 2005-05-12
-- Taken from the net --

Programs that you wish to autostart on KDE startup need to be placed into ~/.kde/Autostart.

Below is an example of autostarting GAIM written in bash. - This was done with nano editor but you can use kwrite or kate or whatever you please.

1) Creat autostart script
```
cd $HOME/.kde/Autostart
nano -w gaim
```
2) Example with Gaim
```
#!/bin/bash
/usr/bin/gaim
```
3)Make script executable
```

chmod +x gaim
```

---

### Post by Amarack on 2005-05-12
Also, a simple symbolic link to the desired application would also work if it was placed in the Autostart directory.

---

### Post by bored2k on 2005-05-12
[QUOTE=Amarack]Also, a simple symbolic link to the desired application would also work if it was placed in the Autostart directory.[/QUOTE]
 I did not know that ... maybe it's because I've been a KDE user for only 4 days.

---

### Post by thom_raindog on 2005-06-03
The symlinks work fine as long as you don't need to add any options to the program. At least I haven't found a way to do that. 
Thats where my problems begin:
I want to start xfishtank and xdesktopwaves at login. symbolic links work fine for both, but I have to add options to the progs.
Thanks to this thread I found a way to do that (I had written a bashscript to start them before but forgot to make it executable *doh*).
What happens is: xdesktopwaves starts with all the options, xfishtank does not start at all.

I had written two seperate scripts, then tried adding the startup for xfishtank to the script that works for xdesktopwaves, nothing changed. Being a bit desperate by now I tried to start xfishtank without options in the script ( /usr/X11R6/bin/xfishtank ) and tried not to use a path at all. Nothing.

If I open a shell and just type 'xfishtank' with or without -d it works fine, using the full path or not...

Any ideas?

---

