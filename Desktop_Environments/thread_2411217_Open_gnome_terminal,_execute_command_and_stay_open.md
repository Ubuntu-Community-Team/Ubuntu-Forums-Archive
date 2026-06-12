---
title: "Open gnome terminal, execute command and stay open?"
date: 2019-01-27
forum: Desktop Environments
---

### Post by marika.alicja on 2019-01-27
Hi,

from command line I'm trying to have Ubuntu open a new gnome-terminal, run tail to view a log file and stay open. Sth like:

```
gnome-terminal -e "tail -f /path/to/file.txt"
```

I'm running in circles, all I find is ppl writing about **-e** and **--command** options, which are deprecated. Appending **-- **doesn't work either. 

The goal is to later put this line in a .sh script which relaunches a local app.

Tried:

```
$ gnome-terminal -e "bash -c 'echo test'"
# Option “-e” is deprecated and might be removed in a later version of gnome-terminal.
# Use “-- ” to terminate the options and put the command line to execute after it.

```

```
gnome-terminal -- /bin/bash -c 'echo test'

```

this does nothing.

---

### Post by TheFu on 2019-01-27
Would you consider using a different terminal?

---

### Post by yetimon_64 on 2019-01-27
> **marika.alicja said:**
> ...
Tried:

```
$ gnome-terminal -e "bash -c 'echo test'"
# Option &#8220;-e&#8221; is deprecated and might be removed in a later version of gnome-terminal.
# Use &#8220;-- &#8221; to terminate the options and put the command line to execute after it.

```

```
gnome-terminal -- /bin/bash -c 'echo test'

```

this does nothing.

After a bit of experimenting here with gnome-terminal, _*in the script try*_  the gnome terminal command as....
```
gnome-terminal -- tail -f /path/to/file.txt 
```

I placed a text file on my desktop and wrote a simple shell script that called the gnome terminal command with tail and the test text file...
[ATTACH=CONFIG]282323[/ATTACH]
The tail command shows the output and the terminal remains open, even after the initial script "test.sh" is finished. Closing down the first terminal leaves the tail output still showing, I have to escape the command with "Ctrl + C" before the terminal will close even with the "Exit the terminal" setting in the command tab of the terminal preferences, this is because the tail command is still running.

In the screenshot above the left hand terminal is showing the contents of the script with the gnome terminal command, the contents of the test text file and the shell script being run. The right hand terminal is the results of the tail command being run in the terminal called from the script.

I worked out the command formatting from the gnome terminal error output in your first post. May be worth another try with the script command calling gnome terminal formatted as in the code box above. Good luck, regards, yeti.

**Edit:** I should also point out I run a custom command prompt, so your terminal will appear a bit different to mine. My custom prompt is set in /home/yetiman/.bashrc. I am using gnome terminal here on ubuntu mate so this may also cause some appearance differences, but the functionality is basically the same as with ubuntu.

---

