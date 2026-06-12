---
title: "Custom &quot;Open With&quot; Commands"
date: 2007-07-18
forum: Desktop Environments
---

### Post by bunnyfly on 2007-07-18
Hello! I'm wondering about the Open With in Nautilus...

I keep getting rpms that I need to convert with alien, so I'm trying to add a custom command. I've found File - Properties - Open With, but I tried typing in "sudo alien." It only showed up as "sudo" in the context menu, and didn't actually run (possibly because it's sitting, taking up ram in a hidden console, waiting for me to type in my password?!)

How can I include a "sudo alien" command and have it displayed as "Alien" or "Convert to DEB" and also run in a visible console? Any help is appreciated!

Also, out of curiosity, why is practically everything compiled into rpms, but Ubuntu doesn't support them? Thanks,
[bunnyfly]

---

### Post by jaffamuffin on 2007-07-18
practically everything isn't compiled as RPMS.

You need to use gksudo alien --whatever...

You could set the root bit on alien - I think that would allow running as normal user (but would run with root privs)

---

### Post by bunnyfly on 2007-07-19
Thank you for you reply! How do I set root bits though? I googled it and almost nothing comes up about root bits. What's the command?

Either way, how could I set a custom menu title? "Convert to DEB" instead of "alien"...

And how does the custom command work - I can't seem to get ANY commands to run on a file through this method. Is this a Nautilus error? Something with my system? Am I just not understanding what a "command" in this context is? Thanks,
[bunnyfly]

---

### Post by jaffamuffin on 2007-07-19
> 
  Thank you for you reply! How do I set root bits though? I googled it and almost nothing comes up about root bits. What's the command?
 
 Either way, how could I set a custom menu title? "Convert to DEB" instead of "alien"...
 
 And how does the custom command work - I can't seem to get ANY commands to run on a file through this method. Is this a Nautilus error? Something with my system? Am I just not understanding what a "command" in this context is? Thanks,
 [bunnyfly]

google for SETUID (set user ID)  the command is chmod. man chmod. Look up linux / unix file permissions for more detail.

I don't know how to do in Nautilus but google for Custom actions in nautilus brings up what looks like easy to follow instructions.


Use Thunar as a file manager - it's better. 

To add an action Right click the file, Open with, custom command, gksudo alien --whatever, and make default.  Should get you started. :)

as for naming, you could put your alien command in a little file like this 
```

#!/bin/bash
gksudo alien --options

```

Then save it as Convert with Alien and chmod +x it, then use that as your custom command.

---

### Post by bunnyfly on 2007-07-20
That's fantastic. Thanks for your help, Jaffa - Thunar is incredible! It has all the naming and command options I need...simple...wonder why Nautilus doesn't...It negates the need for me to mess with scripts or chmod...but at least I know about that now incase I have a use for it later...

I'm glad I can drag files in Thunar to an address bar button to move them to a parent directory! I wondered at Nautilus and how that could have been overlooked!? Thanks,
[bunnyfly]

---

### Post by zweiundzwei on 2007-07-20
I have a similar problem, but couldn't solve it with the directions here.

I have some .md5 files and I'd like to start the terminal when clicking them and execute
md5check /path/filename.md5

How do I do that without installing Thunar?

---

### Post by jaffamuffin on 2007-07-20
> **zweiundzwei said:**
> I have a similar problem, but couldn't solve it with the directions here.

I have some .md5 files and I'd like to start the terminal when clicking them and execute
md5check /path/filename.md5

How do I do that without installing Thunar?


Depends on the program you are using to click on the file. 

You need to create a custom action like above, and make is call this script:

```


#!/bin/bash
xterm -e md5check $1

```

Should work possibly.

---

### Post by zweiundzwei on 2007-07-20
It works! Thanks a lot!

---

