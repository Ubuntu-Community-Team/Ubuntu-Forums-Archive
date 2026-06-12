---
title: "Works in terminal but not launcher?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2006-02-18
I have recently installed SimCity 3000 Unlimited, and got it working, using the commands ```
LD_ASSUME_KERNEL=2.2.4 sc3u
``` through the terminal, and the game starts off without a hitch. However, if I try to create a launcher (no matter what DE), it opens and shuts a terminal with nothing happening, although it is the exact same command. Any ideas?

---

### Post by cilynx on 2006-02-18
More of a hack than a solution:

Make a little bash script of that command such that you can just run the script to start the program.  Make a launcher to run the script.  I've gotten around quite a few difficult apps this way...

---

### Post by TheIdiotThatIsMe on 2006-02-18
[QUOTE=cilynx]More of a hack than a solution:

Make a little bash script of that command such that you can just run the script to start the program.  Make a launcher to run the script.  I've gotten around quite a few difficult apps this way...[/QUOTE]

Unfortunately, I have no idea how to make a bash script, and I do not know how to program :(

---

### Post by cilynx on 2006-02-19
It's much easier than you think.  Just open up a text editor and make a new file called SimCity3000.sh or something like that.  The ".sh" denotes a bash script.

All you need to put in the file is:
```

#!/bin/bash

LD_ASSUME_KERNEL=2.2.4 sc3u

```

You don't even technically need that first line, it's just good form.  Once you make that file, all you have to do to run it is either:

```

bash SimCity3000.sh

```

or make the script executable
```

chmod +x SimCity3000.sh

```

then run the script directly
```

./SimCity3000.sh

```

Once that works, you can make a launcher pointing to your script.

Hope this helps...

---

