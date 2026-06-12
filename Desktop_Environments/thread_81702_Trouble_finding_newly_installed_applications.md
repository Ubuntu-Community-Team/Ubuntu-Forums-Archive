---
title: "Trouble finding newly installed applications"
date: 2005-10-25
forum: Desktop Environments
---

### Post by seatea on 2005-10-25
I seem to be having trouble with what on  the surface appeared to be rather straightforward tasks, like installing applications with Synaptic, so once  again I am asking  for help. I was looking  for a stand alone spelling checker to use for situations  like checking forum posts for typos. I have SpellCatcher in OS 9.2.2 that  I can use in any application without having to open a text editor. I don't know if there is a similar program in Ubuntu, but I did find a stand alone spelling checker, aspell, that I thought I would try. I installed it with Synaptic, but have been unable to find it in any menu. I searched in "Add applications" and it returns "No Results Found". There were no problems at installation. It shows in Synaptic as being installed. I tried "ls aspell" in my home folder with terminal, and it says "no such file or directory". I have had some successful installs of other programs, like Epiphany and the GNOME screen saver. Can someone tell me what the problem is with the install of aspell?

Thanks.

---

### Post by aysiu on 2005-10-25
It looks to me, based on [its documentation](http://aspell.net/man-html/Spellchecking-Individual-Files.html#Spellchecking-Individual-Files), as if aspell is a command-line application. It's not a graphical one like Epiphany.

---

### Post by seatea on 2005-10-25
Thanks aysiu. Allow me a couple of more "duh" questions. How did you determine that this was a command line program? Where did you find the documentation? I don't suppose it would be possible to highlight text in any program and get aspell to check it, would it?

---

### Post by sam hassell on 2005-10-25
If you cannot find the app in the menus, the next thing to try is opening the command line and typing the name of the program (ie. "aspell") followed by Enter.

If that returns a result the program has been installed, although sometimes you may have to try a few variations on the package name to find the program.

You can find more information on command line programs by typing "man" (manual) followed by the name of the application.

ie: "man aspell"

You press "q" to quit this program.

---

