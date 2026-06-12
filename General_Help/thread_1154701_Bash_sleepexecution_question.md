---
title: "Bash sleep/execution question"
date: 2009-05-10
forum: General Help
---

### Post by trpnblies7 on 2009-05-10
I like to listen to music when I go to bed, so I made a very simple script to kill audacious after 30 minutes.

```
#!/bin/bash
sleep 1800
killall audacious
```

Is there a way to specify how long I want the sleep duration to be upon executing the script if I want it to be longer or shorter than 30 minutes? I know very little about scripting, so I don't know if there's a simple way to just have a dialog box pop up where I can type in the length of time I want, click ok, and have the script run.

Any help would be greatly appreciated.

---

### Post by collinp on 2009-05-10
I edited and commented on your script as to what I edited in does:
```

#!/bin/bash
## This prompt will allow you to enter the amount of time you wish for the script to sleep
echo "How long do you wish for the script to sleep:"
## This reads the input as a variable, which will be used to set the amount of time to sleep
read sleep
## The variable is read here
sleep $sleep
killall audacious 
```

You must run this from a terminal, though, as creating a GUI prompt would be getting beyond what Bash can do.

---

### Post by trpnblies7 on 2009-05-10
Thanks! That's very helpful. Is there a way to have the script run in the terminal by double clicking it rather than opening a terminal and typing in the path of the script? I tried having it open with gnome-terminal, but that didn't work.

---

