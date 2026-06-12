---
title: "Open Multiple Apps from bash script"
date: 2010-11-17
forum: Desktop Environments
---

### Post by sbarrow on 2010-11-17
I'm trying to create a bash script that will open firefox, evolution, gedit (specific file), etc. 

For the most part it works, but after it opens evolution or gedit, it pauses execution, until I close that app down. 

I don't want to have this done at login, i want to pick and choose when I open them all. 

Thanks for any help.

---

### Post by tom4everitt on 2010-11-18
I'm pretty sure it is as simple as ending every program launch with a '&'.

So your script would look like this, for example
```

#!/bin/bash

firefox &
evolution &
gedit myfiles &

exit 0

```
(The first and the last line not being quite necessary for most purposes.)

Essentially your script will be one *process*. In this process the each command will be executed in order, each one started when the previous one is done (just like any programming language). 

However, you can *fork* the process with the '&' operator. The command launched with an appending '&' will then be a new process; which, in turn, means that main script process can continue with the next command before the original one is done.

You have probably used the forking operator in the shell (terminal) many times without thinking about what it does. Essentially your shell is just one such process executing commands after each other. So if you launch for example gedit from command line (without forking), your shell will not be receptive to any new command as long as gedit is running. Try it!

Sometimes processes will automatically fork themselves, which makes the story a bit more complicated. Firefox is an examples of this. I think it is launched by a script, in which forking is performed.

---

### Post by sbarrow on 2010-11-18
That was it. thanks for your input and comments.

---

