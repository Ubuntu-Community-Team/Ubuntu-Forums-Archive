---
title: "closing all of the terminal windows at once"
date: 2008-11-13
forum: Desktop Environments
---

### Post by nickstephens on 2008-11-13
Hi all, 

I can not seem to be able to find what I am looking for and I am sure there must be a simple way of doing this that can be included as a shell command. Does anybody know how to shut all of the terminal windows open at the same time. It would be even more useful if this could be done for a particular desktop.

---

### Post by prshah on 2008-11-13
> **nickstephens said:**
> Does anybody know how to shut all of the terminal windows open at the same time.

All terminal windows (emulated terminals) run in a single "parent" process id. If you kill that parent process id, all terminal windows will close instantly.

Try it; open a number of terminals (Applications-Accessories-Terminal) and the give this command
```
sudo kill `ps -e | grep -i gnome-terminal | cut -f 1 -d " "`
```

---

### Post by hictio on 2008-11-13
What's wrong with using 'killall' for this?

Just tested for kicks, added as an alias on my ~/.bashrc:

```

alias kill_term='/usr/bin/killall gnome-terminal'

```

Then, issue:

```

source .bashrc (ENTER)

```

After that, the alias is "live", typed "kill_term" on a Gnome Terminal, and all of them went poof.
Of course, this does not take into account which terminal is in which Virtual Desktop, it simply kills everyone of them.

---

### Post by prshah on 2008-11-13
> **prshah said:**
> 
```
sudo kill `ps -e | grep -i gnome-terminal | cut -f 1 -d " "`
```

> **hictio said:**
> 
```

alias kill_term='/usr/bin/killall gnome-terminal'

```


Once again I have proved that the simplest solution is right beyond my grasp. You are quite right, killall will do the job just as well, and with a great deal less fuss.

---

### Post by nickstephens on 2008-11-14
typical! I was so close. I just didn't try without a space between kill and all. Ah well, done now. cheers for the help 

> **hictio said:**
> What's wrong with using 'killall' for this?

Just tested for kicks, added as an alias on my ~/.bashrc:

```

alias kill_term='/usr/bin/killall gnome-terminal'

```

Then, issue:

```

source .bashrc (ENTER)

```

After that, the alias is "live", typed "kill_term" on a Gnome Terminal, and all of them went poof.
Of course, this does not take into account which terminal is in which Virtual Desktop, it simply kills everyone of them.

---

### Post by spupy on 2008-11-14
Ok, about killing all terms on a specific virtual desktop. You could use the program **wmctrl**. It is used to manage windows from the command line. 
You can use this command:
```
 wmctrl -lp | grep "Term" | grep " NumberOfVirtualDesktop "
```
(note the spaces around the number, they are essential)
To find all windows with "Term" in their title, that are present on a particular virtual desktop. Counting virtual desktops starts from 0. Then you can extend this command to:
```
wmctrl -lp | grep "Term" | grep " 2 " | awk '{print $3}'
```
This will print the process IDs of all windows with "Term" in their title, who reside on the **3rd** virtual desktop. Now you can use **kill**.
This is the complete script:
```
#!/bin/bash
#Argument 1 is the number of the desktop, counting from 0
#If not present, kill terms on all desktops

title="Term"

if [ "$1" = ""  ]
then
	wmctrl -lp | grep "$title" | awk '{print $3}' | while read line
		do
			kill $line
		done
	exit
fi

wmctrl -lp | grep "$title" | grep " $1 " | awk '{print $3}' | while read line
		do
			kill $line
		done
```

---

