---
title: ":q? is there any application like conky for ubuntu as conky is buggy with gnome ?"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by drvista on 2007-09-13
:q? is there any application like conky for ubuntu as conky is buggy with gnome ?

---

### Post by PurposeOfReason on 2007-09-13
How is it buggy? I haven't had any problems with it.

---

### Post by drvista on 2007-09-13
I mean buggy with compiz fusion it overlaps the panles when started with compiz

---

### Post by PurposeOfReason on 2007-09-13
So make a bash script so it starts after compiz. Search the post your conkyrc thread and you would see that fix a lot.

EDIT - ```
#!/bin/bash

sleep 15 &&
conky -d -c /home/YOURUSERNAME/.conkyrc &
exit
```

Then add the location of the script to your sessions for conky.

---

### Post by hyperair on 2007-09-14
Not to nitpick, but when you have the "-d" flag enabled, you don't need to put "&" because Conky forks to the background.

Another thing... You might want to put Compiz and Conky starting up in the same script.. something like this, because sometimes you don't really know how long Compiz takes to start up:
```

#!/bin/sh

compiz --replace -c emerald & # or whatever your compiz command is
sleep 10
conky -d

```

Or if you want a really foolproof way of getting it to start after Compiz, but don't want the two in the same script:
```

#!/usr/bin/perl

while (! `pidof compiz`) { }
sleep(10);
exec("conky");

```

Note, for the second code, I don't know how to do a Bash script for it so I did it in Perl instead. That's not really a problem anyway, since Perl is installed by default.

---

### Post by drvista on 2007-09-14
thanks it works great but i make it 20 seconds

---

### Post by hyperair on 2007-09-15
Yeah like I said, it doesn't work the same on all systems due to a race condition. How long Compiz Fusion takes to start up is rather unpredictable.

---

