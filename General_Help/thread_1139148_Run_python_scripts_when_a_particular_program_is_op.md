---
title: "Run python scripts when a particular program is opened"
date: 2009-04-26
forum: General Help
---

### Post by ninjapirate89 on 2009-04-26
I have a python script that I want to run every time I open Banshee. Is there a way I can do this? Thanks.

---

### Post by ninjapirate89 on 2009-04-26
Bump...also if possible I want the script to stop running automatically when Banshee is closed.

---

### Post by lovinglinux on 2009-04-26
You shouldn't  bump your thread so fast. Please wait at least 24 hours to do it.

You can create a script in bash to launch banshee like this:

```
#!/bin/bash

pythonscript.py &

banshee &&

killall pythonscript.py

exit
```

Replace pythonscript.py with the path to your script. Then, replace the Banshee launcher command with the path to this script.

This script wil launch the python script in the background (&), then launch banshee and wait until it is closed (&&), then kill the pythonscript and exit the terminal.

---

### Post by ninjapirate89 on 2009-04-26
> **lovinglinux said:**
> You shouldn't  bump your thread so fast. Please wait at least 24 hours to do it.

You can create a script in bash to launch banshee like this:

```
#!/bin/bash

pythonscript.py &

banshee &&

killall pythonscript.py

exit
```

Replace pythonscript.py with the path to your script. Then, replace the Banshee launcher command with the path to this script.

This script wil launch the python script in the background (&), then launch banshee and wait until it is closed (&&), then kill the pythonscript and exit the terminal.


Thank you very much this looks like it should work. Also sorry for the quick bump but I was anxious to get this working.

---

### Post by ninjapirate89 on 2009-04-26
Hi sorry to bother again. I have it working when it starts up but when I close Banshee the python script doesn't stop running. Any ideas?

---

### Post by lovinglinux on 2009-04-26
> **ninjapirate89 said:**
> Hi sorry to bother again. I have it working when it starts up but when I close Banshee the python script doesn't stop running. Any ideas?

Open the System Monitor and check the complete path to the pyhton script. It should start with "python /home/user/blablabala". I don't know if it will work, but this is my best guess.

---

### Post by ninjapirate89 on 2009-04-26
The path in my script matches the path that System Monitor shows. Here is the script in case I made an error.
```
#!/bin/bash

/home/ninjapirate/.CoverGloobus/CoverGloobus.py &

banshee &&

killall /home/ninjapirate/.CoverGloobus/CoverGloobus.py

exit

```

Should it maybe be written like this?
```

killall python /home/ninjapirate/.CoverGloobus/CoverGloobus.py

```

Edit -> Just tried writing it as I posted above and it works now. Thanks for all your help.
Edit2 -> LOL. I should have read your post more carefully. I just noticed that is what you put. Whoops!

---

### Post by lovinglinux on 2009-04-26
You are welcome. Have fun.

---

