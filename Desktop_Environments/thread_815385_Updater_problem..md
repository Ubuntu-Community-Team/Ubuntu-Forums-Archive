---
title: "Updater problem."
date: 2008-06-01
forum: Desktop Environments
---

### Post by denfoote on 2008-06-01
When Hardy updates, I get this error message:

E:g15daemon: sub processes post-installation script returned error exit status 1

What is going on here???

How do I fix it??

I'm currently running Linux within Windows XP SP3.

The next time Hardy updates, I'll remember to take a screenshot of the terminal!! Like an idiot, I forgot to do that!!

---

### Post by Victormd on 2008-06-01
Do you have the proposed repos marked under software sources? If so, unmark it, open a terminal window and run
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

and see if it outputs any errors. If not, re-mark proposed repos and run the above commands again and see what the output is...
Earlier, the proposed repos was giving an error but now it seems to be fixed (at least on my comp.)...

---

### Post by denfoote on 2008-06-01
> **Victormd said:**
> Do you have the proposed repos marked under software sources? If so, unmark it, open a terminal window and run
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

and see if it outputs any errors. If not, re-mark proposed repos and run the above commands again and see what the output is...
Earlier, the proposed repos was giving an error but now it seems to be fixed (at least on my comp.)...

Ok. Thanks for the info.
I'm not sure what to do with it as I'm still kinda new at this Linux thing.
The error was with the very first update after installing the OS.
The strange thing is that with my Vista machine I do not get this error message, so I'm thinking it's some kind of conflict with XP SP3.

If you could walk me through this, I'd appreciate it.

---

### Post by denfoote on 2008-06-01
Here are shots of the terminal.

[IMG]http://img.photobucket.com/albums/v22/denfoote/Screenshot.png[/IMG]


[IMG]http://img.photobucket.com/albums/v22/denfoote/Screenshot-1.png[/IMG]

---

### Post by Victormd on 2008-06-02
Does this happen all the time? I will get a similar error every now and then and believe it's related to the repository server load because the error is not constant. I wouldn't worry about it unless you get the same error everytime you try to update...

---

