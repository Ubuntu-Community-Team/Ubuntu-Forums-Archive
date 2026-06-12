---
title: "shell script to start program in other language"
date: 2008-03-27
forum: Desktop Environments
---

### Post by nlz on 2008-03-27
my girlfriend likes it to have Gimp in Dutch. Normally you'll have to type in the terminal:
```

LANGUAGE=nl gimp
```

but she just doesn't want to remember this. So how can i make a shell script that can be run by a icon on the taskbar? If i put this line in the command line of the icon, it won't work. I composed a shitty script, but it doesn't work...

```
#!/bin/bash
LANGUAGE=nl gimp
exit
```

what should i change?

---

### Post by diegosouza on 2008-03-27
Hey man, I think you could create or alter the default launcher like it:

MYVAR=value && gimp

so it sets $MYVAR and launch gimp. Do it and send us a reply  :-)

---

### Post by nlz on 2008-03-27
i just changed the launcher command to LANUAGE=nl && gimp and got

```
Could not launch application
Failed to execute child process "LANGUAGE=nl" (No such file or directory)
```

sorry if i didn't get it.

I also tried (just to be sure) MYVAR=LANGUAGE=nl && gimp with the same outcome

---

### Post by DuncanNZ on 2008-07-03
This solution might be easier:

"running app in a different language": [http://ubuntuforums.org/showthread.php?t=138015](http://ubuntuforums.org/showthread.php?t=138015)

---

