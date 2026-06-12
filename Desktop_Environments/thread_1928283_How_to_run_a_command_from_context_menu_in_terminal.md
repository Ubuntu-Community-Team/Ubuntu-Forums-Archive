---
title: "How to run a command from context menu in terminal?"
date: 2012-02-19
forum: Desktop Environments
---

### Post by frytek on 2012-02-19
I would like to convert, say, flv files to mp3 by right-clicking on them. 
It is quite simple to configure nautilus-action (or actually thunar-action, because I use Xubuntu) - but the command runs in background. I can watch the mp3 file appear and grow, but in fact I don't know if the processing is finished. 
I would like to see a(ny) terminal window pop-up with the running command. 

I was trying to find it in google but all I can find is only "how to add 'open terminal here' to context menu", so maybe somebody here can tell me how to do this? 

Thanks,

---

### Post by Dreamer Fithp Apprentice on 2012-02-19
With gnome-terminal I think it would work to make the command "gnome-terminal -e whatever-command-u-use-to-convert symbol-for-target-file" without the " marks and substituting the command you use & whatever thunar actions call the selected file. If you don't use gnome-terminal you might try it anyway. And if it doesn't work in whatever terminal you use you could try "command-to-invoke-the-terminal-of-your-choice --help" or even "man terminal-invocation-command" to see if it has a similar switch.

I'm no expert but this pattern works for me in a similar situation.

---

### Post by frytek on 2012-02-20
Well, in general, it works. I mean, it pops up a terminal with a script in it. But it doesn't pass the filename to the script. 

Normally the script would be called "script file"
So as action I defined gnome-terminal -e /path/to/script %f 
But the script in the terminal claims there's no file to work on...


I worked it around by adding gnome-terminal -e to the script itself,  which works nice, although I guess it's not exactly how it should be done. :) 
Thanks,

---

### Post by LewisTM on 2012-02-20
If you want to run a program in a terminal with multiple parameters you have to use quotes e.g.
```
xfce4-terminal -e "yourscript %f"
```
or the terminal will think you have more than one parameter for it.

One more tip (you may already know this): if you want the terminal to wait for a key press at the end of a script, so you don't lose the output, add this command before exiting
```
read -p END-OF-SCRIPT
```
You can replace the end-of-script with "Press any key to continue..." etc.

Cheers!

---

### Post by frytek on 2012-02-20
Thank you, it worked.I would never think that using quotes would pass %f as an argument. ;)

---

### Post by LewisTM on 2012-02-20
NP
It seems that Thunar just searches for %f and replaces it with the given filename.
Please mark as Solved.

---

