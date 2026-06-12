---
title: "Conky conkyrc help?"
date: 2013-03-13
forum: Desktop Environments
---

### Post by slokenafk on 2013-03-13
Hello all.

I have been trying desperately to configure conky for some time now.  I must be missing something.  When I run conky through terminal, processes never stop running.  If I close the window it just reminds me of this.  On top of this no matter how hard I try to edit my .conkyrc file conky will not change.  Any suggestions or help is appreciated.

running ubuntu 12.10

EDIT: I believe that conky is not reading my conkyrc file but rather the original config.  How can I change this??

---

### Post by Frogs Hair on 2013-03-13
Default conky appears as a black box on the top left of the screen . To get a _basic_ conkyrc to run. place it in home with out a folder and rename it .conkyrc  then close nautilus and start conky . Renaming will move the text document to hidden folders and it can be located by using Ctrl + H.
 
Copy and paste the conkyrc to this thread and  I will test it out. :)

---

### Post by Frogs Hair on 2013-03-13
Some times if the x and y placement is not set within the screen size limits the conky will not be visible. I have seen this when using conky made for a larger monitor than my own.

---

### Post by slokenafk on 2013-03-13
Im using the default conkyrc.  The problem is even if I make alterations It is still showing the original.  For example.  I changed where it says to show my username, computer name, and distro.  Yet it still appears as the standard conky setup. :-k

---

### Post by slokenafk on 2013-03-13
Ok Im getting somewhere.  I loaded a new conkyrc file and....

Now I have two conky(s)? Im not sure where the default one is loading from.

[IMG]http://i1296.photobucket.com/albums/ag3/Koshyk/Screenshotfrom2013-03-13142850_zps706fdf45.png[/IMG]

---

### Post by Frogs Hair on 2013-03-13
Post the rc because I am not sure what you mean by default. I don't know why the one on the left is appearing . try```
killall conky
``` and restart.

---

### Post by deadflowr on 2013-03-13
I usually( that is when I do launch conky) launch it with alt+f2 to open the runner/command launcher.
You can actually name your conky script anything you want, if you use the config command to launch it.
```
conky --config path/to/file
```

I also throw a killall conky in the runner, as it saves the most recent commands.

---

### Post by slokenafk on 2013-03-13
Reboot fixed everything.  Thank you.

---

