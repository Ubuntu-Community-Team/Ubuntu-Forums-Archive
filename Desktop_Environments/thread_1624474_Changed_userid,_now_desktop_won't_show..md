---
title: "Changed userid, now desktop won't show."
date: 2010-11-17
forum: Desktop Environments
---

### Post by McFatty on 2010-11-17
Hi,

**Experience with Ubuntu**: I know basic commands in the terminal. (ls, pwd, cd, sudo halt, mkdir, and a few others) 

**Premise**:
My terminal opened with this line:

**Bilbo**@host:/$

I wanted it to open with THIS line:

**Frodo**@host:/$

So I went to the System menu, administration, user options. I'm not exactly sure of every button I pushed but the general gist of what I did was change the username in the home folder from **Bilbo **to **Frodo**.

A prompt came up and asked if I wanted to delete the old folder (the **Bilbo **folder). It also said that if I was duplicating it but giving it a new name (**Frodo**), it was ok to delete the old one (**Bilbo**) because I would still have all the files. I checked the box that said "Delete old folder." Then I clicked the button that said copy folder under new name (**Frodo**).

**Problem**:
The system boots. I can log in. The desktop is empty. Nothing there. I can open a terminal with ctrl+alt+T.

Upon login, 3 windows pop up.

The First:
Could not update ICEauthority file /home/**Bilbo**/.ICEauthority

The Second:
Problem with configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

The Third:
Nautilus could not create the following required folders /home/**Bilbo**/Desktop, /home/**Bilbo**/.nautilus. Before running Nautilus create these folders, or set permissions such that Nautilus can create them.

Now, I went to the library to try to fix this and found this page

[http://art.ubuntuforums.org/showthread.php?p=8061988](http://art.ubuntuforums.org/showthread.php?p=8061988)

so I tried to run the commands there. The only one that worked was

sudo chmod 644 /home/**Frodo**/.ICEauthority

How can I fix this?

Peace and Love,
-McFatty

---

### Post by asmoore82 on 2010-11-17
Check the output of ```
cat /etc/passwd
```

A line similar to this one of mine is what you're looking for...
```
asmoore:x:1000:1000:Adam Moore,,,:/home/asmoore:/bin/bash
```

---

### Post by McFatty on 2010-11-17
This has been resolved.

FYI the solution:

sudo mv /home/Frodo /home/Bilbo

I am now ever so slightly less of a noob.

Peace and Love
-McFatty

---

