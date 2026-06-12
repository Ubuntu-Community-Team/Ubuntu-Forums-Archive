---
title: "auto-running a script when open app?"
date: 2009-03-17
forum: General Help
---

### Post by Jameshardy88 on 2009-03-17
Hi, i was wondering if it is possible and how i would go about setting up a script to run automatically when i open a certain program?

Basically i have a conky script that shows the lyrics to whichever song i happen to be playing, so i wanted it to open whenever i opened rhythmbox. I already have a script that will open it i just want to set it that it will automatically run when i run rhythmbox

Thanks for any help, James

---

### Post by sedawk on 2009-03-17
Why not to use a wrapper script and pass on all 
arguments to your mp3 player?

I think a more straight forward solution would be to look for
a plug-in for your mp3 player that shows song lyrics every
time you play a new song!

---

### Post by Jameshardy88 on 2009-03-17
sorry im a bit new to all this what is a wrapper script?

---

### Post by sdennie on 2009-03-17
First:

```

cd
mkdir -p bin

```

A wrapper script is something like this:

```

#!/bin/bash

/usr/bin/rhythmbox "$@" &
your_custom_script

```

Save it as ~/bin/rhythmbox and then:

```

chmod +x ~/bin/rhythmbox

```

Now when you run rhythmbox, you will actually be running your wrapper script.

---

### Post by Jameshardy88 on 2009-03-17
Do you mind explaining what all the stages do? The first one i am clueless about. Is the second one basically just modifying the existing rhythmbox launch script and the third activating it?

---

### Post by sdennie on 2009-03-17
> **Jameshardy88 said:**
> Do you mind explaining what all the stages do? The first one i am clueless about. Is the second one basically just modifying the existing rhythmbox launch script and the third activating it?

Sure:
```

cd             # Make sure you are sitting in ~
mkdir -p bin   # Create a bin directory, don't care if it doesn't exist

```

```

#!/bin/bash

/usr/bin/rhythmbox "$@" &  # Run rhythmbox with the arguments given to the script and put it in the background
your_custom_script         # Run your script

```

Save it as ~/bin/rhythmbox (You are doing this because ~/bin is checked for binaries before /bin and /usr/bin)

```

chmod +x ~/bin/rhythmbox # Make your new script executable so that it overrides the rhythmbox executable (which you explicitly call in the script).

```

Hope that helps.

---

