---
title: "Lubuntu desktop shortcut to run script"
date: 2015-04-26
forum: Desktop Environments
---

### Post by jonathan81 on 2015-04-26
I have a file on my desktop called run_ipython.sh. It contains:

```
#!/bin/sh


ipython notebook

```

If I open a terminal, I can run the script successfully using:

```

sh run_ipython.sh
```

What I want to do is create a desktop shortcut that runs the script.

So I have made a file called run_ipython.desktop that contains this:

```
[Desktop Entry]
Name=IPython Startup
Exec=sh /home/jon/Desktop/run_ipython.sh
Type=Application
Terminal=false

```

However, when I double click on the icon for that, nothing happens.

I have also tried double clicking on the run_ipython.sh icon on my desktop. When I do that, a window pops up asking me if I would like to Execute, or Execute in Terminal. Neither of those do anything either.

I have attempted to chmod the script. Inside the file permissions, next to Execute: I have specified Anyone. So I hope the file is executable.

---

### Post by CantankRus on 2015-04-26
Try just using ....
```
[Desktop Entry]
Name=IPython Startup
Exec=**ipython notebook**
Type=Application
Terminal=false
```

The script just runs a single command so may as well just use the command in the .desktop file.
Not familiar with IPython but maybe you should also run in terminal ....eg  "Terminal=**true**"

---

### Post by jonathan81 on 2015-04-26
Thanks for the tip CantankRus. Strangely, my problem went away after I rebooted my machine.

---

