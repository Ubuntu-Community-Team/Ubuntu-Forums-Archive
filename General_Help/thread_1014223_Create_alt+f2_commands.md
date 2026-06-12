---
title: "Create alt+f2 commands???"
date: 2008-12-17
forum: General Help
---

### Post by N00b-un-2 on 2008-12-17
Whenever I install a program not using synaptic/add-remove programs/terminal, like almost any program downloaded from the Internet (games, etc.) you have to navigate to wherever you installed the app on your computer to open it.  I'm wondering how (I'm sure there has to be a way) to add those programs to the list of known applications and assign it a shortcut (for use with alt+f2, or when creating a launcher).  For example, I installed Urban Terror, a very popular FPS game on Linux that is not available for download in the repos.  I can create a launcher for it, but instead of just being able to hit alt+f2 and enter "urban-terror", I have to enter a command like "sudo /usr/share/apps/ioUrbanTerror/ioUrbanTerror.i386" to launch the program.  I've tried the alias command, but that only works in the terminal.
eg; alias urban-terror="/usr/share/apps/ioUrbanTerror/ioUrbanTerror.i386" urban-terror
If, for instance, I wanted to create a launcher for a specific game for an NES emulator, how would I go about creating the "nintendo" command if I wanted to be able to launch the nes emulator my entering alt+f2 "nintendo" (or likewise in the terminal).  I've created launchers like this for .pdf files that I access regularly by entering "evince ~/Documents/studyguide.pdf" to launch the studyguide with the program evince.
any help with this would be appreciated.

---

### Post by kanikilu on 2008-12-17
Can you not just make a symlink to it and put the link somewhere in your path (e.g. /usr/bin)?

For instance:

```
cd /usr/bin
sudo ln -s /usr/share/apps/ioUrbanTerror/ioUrbanTerror.i386 urban-terror
```

---

### Post by ibuclaw on 2008-12-17
Urban Terror is available from getdeb.net

[http://www.getdeb.net/search.php?keywords=Urban+Terror](http://www.getdeb.net/search.php?keywords=Urban+Terror)

That comes with file menu entries, etc...

Else, you could always just put together a script:
```
sudo gedit /usr/games/urbanterror
```
And paste this in:
```
#!/bin/bash
cd /usr/share/apps/ioUrbanTerror/
./ioUrbanTerror.i386

```

Regards
Iain

---

