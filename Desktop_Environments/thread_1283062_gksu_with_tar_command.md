---
title: "gksu with tar command"
date: 2009-10-05
forum: Desktop Environments
---

### Post by spedgenius on 2009-10-05
I am having a problem using gksu with the tar command
i have set up a bash file with the line

gksu tar cpzf /backup/backup.tar -X /backup/exclude  / 2>/backup/error.log

It outputs a log file for gksu saying -X is not a recognised command for gksu.  basically from what i can tell it is using the tar options as gksu options.  I am setting up a computer for a rather linux illiterate friend and I want the simplest backup/restore solution that he can execute from the system menu.  currently i can get it to work with replacing gksu with su, and running the bash in the terminal from the menu.  but that isnt as pretty:?

---

### Post by renkinjutsu on 2009-10-05
a backup using tar would have to be done on a liveCD, because the files under / are constantly changing and tar will output a bunch of errors.. so probably be a good idea to exclude /var /dev and /proc also..

try```
tar -cpzf
``` instead

if nothing works, you can just setup rsync and cron for him, that way he doesn't have to do anything

---

### Post by kerry_s on 2009-10-05
you shouldn't be using graphical root for a bash command.

i suggest calling the terminal to execute the command.

example:
[B]gnome-terminal -x sudo tar cpzf /backup/backup.tar -X /backup/exclude / 2>/backup/error.log
[/B]
or

**gksudo "gnome-terminal -x tar cpzf /backup/backup.tar -X /backup/exclude / 2>/backup/error.log"**

---

### Post by renkinjutsu on 2009-10-05
or save the tar command as an executable file and make a launcher for it with this is at the command

gksu *executable*

---

### Post by lavinog on 2009-10-05
> **renkinjutsu said:**
> or save the tar command as an executable file and make a launcher for it with this is at the command

gksu *executable*

+1
This would make the most sense, and will be easier to maintain.

---

### Post by spedgenius on 2009-10-05
thanks for the replies, of couse the exclude file has excludes for all the virtual folders as well at mounted mnt and media.

also, I am not trying to run the full command from the launcher just the script.

I have tried using the gksu command from the launcher, as suggested but,  it prompts for password but the script never runs. the log file doesnt get created.  if i remove the gksu and just run the script in the launcher then it runs, just not with root permissions.

that is when i tried putting the gksu command in the script as mentioned before.

If i have to run the script in terminal thats fine, but i would really like to use gksu to launch the script if possible.

---

### Post by renkinjutsu on 2009-10-05
> **spedgenius said:**
> thanks for the replies, of couse the exclude file has excludes for all the virtual folders as well at mounted mnt and media.

also, I am not trying to run the full command from the launcher just the script.

I have tried using the gksu command from the launcher, as suggested but,  it prompts for password but the script never runs. the log file doesnt get created.  if i remove the gksu and just run the script in the launcher then it runs, just not with root permissions.

that is when i tried putting the gksu command in the script as mentioned before.

If i have to run the script in terminal thats fine, but i would really like to use gksu to launch the script if possible.

make a symlink of your script to /usr/sbin ;)

---

### Post by spedgenius on 2009-10-05
> **kerry_s said:**
> you shouldn't be using graphical root for a bash command.

i suggest calling the terminal to execute the command.


**gksudo "gnome-terminal -x tar cpzf /backup/backup.tar -X /backup/exclude / 2>/backup/error.log"**


actually I just tried that and it worked. thanks

---

