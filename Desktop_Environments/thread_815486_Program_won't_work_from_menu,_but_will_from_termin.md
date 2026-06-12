---
title: "Program won't work from menu, but will from terminal?"
date: 2008-06-01
forum: Desktop Environments
---

### Post by underwater on 2008-06-01
Hello,  I downloaded the most recent processing.org language to play around with and I ran into this odd bug.


If I cd into the folder using terminal and run the program, the GUI window appears and everything works as normal.  When I make a menu item for it, however, this doesn't happen.  Nothing comes up.  I even tried run Application in Terminal, but the terminal window appears and then closes before I can get any useful information.

Again, the program works if I just open a terminal and then do it.  


Any ideas?

Thanks,

---

### Post by angry_johnnie on 2008-06-02
Given that cd'ing into the app's directory and then running it will open it, you could try changing the command that is used to launch it in the menu, to something like this:


```
gnome-terminal --command=/path/to/the/app
```

You could try alt + f2 and then the above, just to see whether it's going to work or not.

---

