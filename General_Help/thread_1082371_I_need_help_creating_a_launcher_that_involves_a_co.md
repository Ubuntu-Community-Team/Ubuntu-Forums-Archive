---
title: "I need help creating a launcher that involves a command line . . ."
date: 2009-02-27
forum: General Help
---

### Post by thrasher6900 on 2009-02-27
I want to create a launcher that opens a terminal and executes this command

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
( I have to oped skype this way in order for my cam and mike to work)

Thanks ahead of time.

---

### Post by damis648 on 2009-02-27
In the command field:
```
gnome-terminal -x 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```
:popcorn:

---

### Post by thrasher6900 on 2009-02-27
> **damis648 said:**
> In the command field:
```
gnome-terminal -x 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```:popcorn:
I tried it and I got this message


> There was an error creating the child process for this terminal

---

### Post by ibutho on 2009-02-27
Create a script e.g. runskype and put the commands below
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

```
Make the script executable (e.g. chmod +x runskype). You can then run skype by doing ./runskype from the directory containing the script or put the script somewhere in your path e.g. /usr/local/bin and you can then just enter "runskype" in a terminal. You can even make a menu or desktop entry for runskype if you wish.

---

### Post by thrasher6900 on 2009-02-27
> **ibutho said:**
> Create a script e.g. runskype and put the commands below
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

```Make the script executable (e.g. chmod +x runskype). You can then run skype by doing ./runskype from the directory containing the script or put the script somewhere in your path e.g. /usr/local/bin and you can then just enter "runskype" in a terminal. You can even make a menu or desktop entry for runskype if you wish.It didn't do the function that the command line was for, which was being able to detect my cam.

---

### Post by ibutho on 2009-02-28
If Skype just needs access to the libraries in /usr/lib/libv4l, try
```
sudo ln -s /usr/lib/libv4l/* /usr/local/lib/.
```
After that try running skype and see if the camera is detected.

---

### Post by thrasher6900 on 2009-02-28
> **ibutho said:**
> If Skype just needs access to the libraries in /usr/lib/libv4l, try
```
sudo ln -s /usr/lib/libv4l/* /usr/local/lib/.
```After that try running skype and see if the camera is detected.Nope.  Still isn't detected unless I enter 
```


LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
``` In the terminal manualy.

The script didn't work either.

---

### Post by thrasher6900 on 2009-03-09
Bump

Anybody have a better answer???

---

### Post by snova on 2009-03-09
> **ibutho said:**
> Create a script e.g. runskype and put the commands below
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

```
Make the script executable (e.g. chmod +x runskype). You can then run skype by doing ./runskype from the directory containing the script or put the script somewhere in your path e.g. /usr/local/bin and you can then just enter "runskype" in a terminal. You can even make a menu or desktop entry for runskype if you wish.

This was pretty close, however the script should be:

```

#!/bin/bash
**export** LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

```

Because variables are not propogated to child processes without using export.

---

### Post by thrasher6900 on 2009-03-10
> **snova said:**
> This was pretty close, however the script should be:

```

#!/bin/bash
**export** LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

```Because variables are not propogated to child processes without using export.
THANK YOU THANK YOU THANK YOU

*dances with glee*

---

