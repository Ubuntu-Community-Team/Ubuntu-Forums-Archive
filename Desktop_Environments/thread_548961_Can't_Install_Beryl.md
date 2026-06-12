---
title: "Can't Install Beryl"
date: 2007-09-11
forum: Desktop Environments
---

### Post by goofeyfoot on 2007-09-11
Am trying to install Beryl.

Feisty Fawn.  AMD machine.

Anyway someone was saying how to install it and somewhere in there you had to change the "sources" file.  Don't know much about this linux stuff and probably never will if I don't get linux running.  Which is circular, I know.

So when I changed this sources file, I couldn't even edit it properly and screwed the whole thing up as a result.  The edit didn't work like normal editing.

Now I get this error.

E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Tue Sep 11 22:10:27 2007
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: michael-desktop
        process ID: 9876
While opening file "/etc/apt/sources.list"
             dated: Sat Sep  8 15:45:04 2007

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.
"/etc/apt/sources.list" 43 lines, 2370 characters
Press ENTER or type command to continue

What the heck do I do now, and more to the point, how the heck do you install this beryl business.  Boy for a handy tool it sure is a bear to install.

Thanks.

Michael

---

### Post by benerivo on 2007-09-12
You don't have to change your sources list to get beryl. Just open a terminal and enter ```
sudo apt-get install beryl && install beryl-manager
```

Your sources list is just a file poniting to sites on the internet where the package manager looks to see what programs and packages are available for installation, and i think beryl is in one of the locations in the default list. You should not have edited it! Just go in to Software Sources from the main menu and make sure all the entries are ticked, then run the code above.

---

### Post by ITAndrew on 2007-09-12
I had this preinstalled when I installed from the live CD. Although I was using Mint, and am not sure if that is specifically a Linux Mint thing.

---

