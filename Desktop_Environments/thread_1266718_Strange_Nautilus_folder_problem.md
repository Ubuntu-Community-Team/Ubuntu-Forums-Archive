---
title: "Strange Nautilus folder problem"
date: 2009-09-14
forum: Desktop Environments
---

### Post by James M Weir III on 2009-09-14
I'm not entirely sure what caused this issue as I was modifying several things earlier today.  But shortly after doing an update and rebooting I ran into a strange issue with Nautilus.

When I went to Places in the main menu and chose any folder (home/desktop/documents, etc) it would give me an error that it couldn't find the location [file:///home/jimmy/documents].  I verified that the folders were all still there.  When I opened the filesystem Nautilus launched just fine and I could navigate to those folders just fine.

So I did a little research and followed what appears to be an outdated method of changing the default action for opening folders in Nautilus.  I later found out that you apparently can't change that default action (at least not in any GUI menu).  But in the process I went to Open With > and as a test just picked gedit to see if it would change the behavior of the Places menu.  It did... So now whenever I open any folder from a launcher it attempts to run the directory in gedit.

I've tried removing/reinstalling nautilus, I've tried moving the config files in my directory, and I've searched everywhere for a file containing the 'gedit' setting.  Attempting to have Nautilus Open With > another program does nothing.  So apparently I've somehow changed the default behavior to gedit and cannot change it / reset it.

Any ideas?

---

### Post by quixote on 2009-09-16
Officially, changing values in /etc/gnome/defaults.list should allow you to alter that behavior. ```
gksudo gedit /etc/gnome/defaults.list
```  But I looked in my own defaults.list, and nautilus isn't even in there, so I don't think that's it.

You say "When I opened the filesystem."  What do you mean, exactly?  Mounted a partition?  Ran "ls" in a terminal?  Clicked on a folder in nautilus?  

Also, what is the "outdated method"?  I didn't think using "Open With" was outdated, so you mean something else, is that right?

---

