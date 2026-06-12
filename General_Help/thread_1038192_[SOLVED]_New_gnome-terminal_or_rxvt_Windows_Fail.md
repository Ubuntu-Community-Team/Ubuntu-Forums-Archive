---
title: "[SOLVED] New gnome-terminal or rxvt Windows Fail"
date: 2009-01-12
forum: General Help
---

### Post by Jesdisciple on 2009-01-12
I have a bash program running in the background from startup to open a new AllTray/Sunbird session when I close the current one, to keep Sunbird's RAM usage low.  For whatever reason, I sometimes need to stop and/or restart the bash process itself.  This requires that I run a separate bash script to change a file's contents, signaling that after Sunbird is exited the first bash process should finish.

I sometimes forget to run this second script before restarting, so I want to display a reminder when that happens.  From reading **gnome-terminal --help**, I thought this should do it:```
gnome-terminal -x read -p "Sunbird is already open!";
```That opens a blank terminal window with an alert dialog, "There was an error creating the child process for this terminal."  I searched for that message and found that it's related to udev, so I reinstalled that (as someone else was instructed).  I also installed **rxvt** and tried this:```
rxvt -e read -p "Sunbird is already open!"
```But that window just closes right after opening (the same thing **gnome-terminal** does if I just use **echo**).  What am I doing wrong?

On the other hand, if I could just kill the first bash process without any user action that would be a better solution...  That would probably require root privileges; can I start my script as root on startup?

---

### Post by mcduck on 2009-01-12
How about using Zenity to display the message instead of opening a terminal for it:

```
zenity --warning --text='Sunbird is already open!'
```

---

### Post by Jesdisciple on 2009-01-12
Thanks!  That did occur to me after I posted, but I didn't even know bash had GUI libraries.

In case anyone knows how to kill a process from bash, please ignore the [SOLVED] tag; that would be a much more user-friendly (well, me-friendly) solution.

---

