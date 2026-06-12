---
title: "Clear entries in &quot;ALT + F2&quot; newb"
date: 2009-05-05
forum: General Help
---

### Post by lesodk on 2009-05-05
how do i delete some entries, that auto completes in the run application "ALT F2".

---

### Post by geirha on 2009-05-05
It reads the PATH environment variable (view it by running "echo $PATH" in a terminal) which contains a set of directories delimited by ':'. It finds all executables in those directories and uses them to auto-complete in the run dialog. In other words, you would have to uninstall the application to have it removed from the auto-completion list of the run dialog ...

---

### Post by lesodk on 2009-05-05
Thanks. My problem is that i have installed matlab.
When i press ALT F2 it autocompletes to "matlab". But i want to autocomplete to  "matlab -desktop". How can i do that, without having to uninstall matlab.

---

### Post by geirha on 2009-05-05
One way would be to create a script that executes "matlab -desktop". You could call it something like matlabdesktop or maybe just md.

The script should look like:
```
#!/bin/sh
exec matlab -desktop
```

Make sure you make it executable, then copy it to the same place as the matlab executable is located (Type "which matlab" to see where matlab is located)

After that you should be able to just type md (if you called it md), or have it autocomplete when you type "matlabd" (if you called it matlabdesktop)


Though, why not just make a launcher on your desktop? Right click the desktop and choose Create Launcher...  Set the Command to "matlab -desktop".

---

### Post by lesodk on 2009-05-05
Thanks. That's solves my problem.
Then it is impossible to clear the autocomplete history in a easy way?

---

### Post by geirha on 2009-05-05
> **lesodk said:**
> Thanks. That's solves my problem.
Then it is impossible to clear the autocomplete history in a easy way?

No easy way that I know of at least.

---

### Post by home jobs on 2009-05-05
You may wish to have a look at the G15tools website ([http://www.g15tools.com](http://www.g15tools.com)),  they have support forums over there. I wish I could be of more assistance, in  that area.Yes, I'll post there, I guess. But you have been a great help, thank  you! :)

You may wish to take a look at mouse settings under the control  center and see you can adjust some settings that way.

system >  Preferences > Mouse

Else You may wish to try Google and see what you  can come up with for your mouse.I couldn't find anything in the preferences and  Google wasn't much help either. It's not a big deal right now, maybe I'll figure  it out later. 

Wish I could help further, but I'll be honest with you The  LCD on my G15 works great, but I to was never able to get the gkeys working.  Which sucks as I would like to be able to configure some compiz shortcuts using  them. I have heard people have more success with the G11 gkeys though, hence my  reason for sending you in that direction.

AngelI'll try to work on it  some more and let you know how it goes.

---

### Post by CatKiller on 2009-05-06
> **lesodk said:**
> Thanks. My problem is that i have installed matlab.
When i press ALT F2 it autocompletes to "matlab". But i want to autocomplete to  "matlab -desktop". How can i do that, without having to uninstall matlab.

Why would you need to uninstall matlab?

It's not like you can't keep typing in the Run dialogue. Let it autocomplete as much as you don't want to type, and then put -desktop at the end. The Run dialogue remembers commands that you've entered, so having typed it in once you only need to press the down arrow key to bring the command back next time you want to run it.

---

### Post by lesodk on 2009-05-06
i have created a script

#!/bin/sh
exec matlab -desktop

but where should i place it?

---

### Post by Brandon Williams on 2009-05-06
> **lesodk said:**
> Then it is impossible to clear the autocomplete history in a easy way?

You just have to unset the gconf key used to store the history:
```
$ gconftool-2 --unset /apps/gnome-settings/gnome-panel/history-gnome-run
```

---

### Post by geirha on 2009-05-07
> **lesodk said:**
> i have created a script

#!/bin/sh
exec matlab -desktop

but where should i place it?

Alongside the matlab executable, or well, anywhere in path really. /usr/local/bin is a good place too. Hit Alt+F2, run ```
gksu nautilus /usr/local/bin
``` and drag the script over to that window.

---

### Post by Brandon Williams on 2009-05-07
If all you're trying to do is get this particular command line to show up in the drop-down list in the Alt+F2 window, then I suggest that you go back to your original idea. There's no need for the script.

Just press 'Alt+F2' and type in the command line you're trying to run. The most recently run command is the one that will show up in the command entry field the next time you press 'Alt+F2' to open the dialog, and all commands ever run through the dialog will show up in the picklist. If you don't want the top entry, just press the arrow key to scroll down through the list. If this is a command that you run regularly from the grun dialog, it will be one of the first ones that you see.

In my opinion, auto-completion in the grun dialog is useful for commands that you rarely run, but for commands that you run often, the picklist is easier. 'Alt+F2' and a couple presses on the down-arrow is generally all that I need for commonly run commands, and it's easier than creating a script for every specific command line that you want to run regularly.

---

