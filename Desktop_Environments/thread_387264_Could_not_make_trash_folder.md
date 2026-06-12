---
title: "Could not make trash folder"
date: 2007-03-18
forum: Desktop Environments
---

### Post by torswin on 2007-03-18
Every time I start my computer and log in, i get this error message:

KDE panel:
Could not make folder /home/torswin/.local/share/Trash.

It is rather annoying... I am running kubuntu.


Pleeease help me [-o<

---

### Post by AtrejuT on 2007-03-18
what happens if you create that folder manually?
navigate to /home/torswin/.local/share
new folder Trash
or in a command line
mkdir /home/torswin/.local/share/Trash

---

### Post by torswin on 2007-03-18
I get the error:

torswin@torswin-desktop:~$ mkdir /home/torswin/.local/share/Trash
mkdir: cannot create directory `/home/torswin/.local/share/Trash': Permission denied
torswin@torswin-desktop:~$ 


looks like i got to change the permissions :S how do i do that?

---

### Post by AtrejuT on 2007-03-18
ok, can you do
```

ls -l /home/torswin/.local/

```

basically there are two options. 
a) you are not the owner of that folder. You should be, though, since it is in your home directory. You change it by running
```

sudo chown -R torswin /home/torswin
sudo chgrp-R torswin /home/torswin

```
This sets you as user and your group for all subfolders of /home/torswin.
b) you don't have write permissions. These can be changed using
```

sudo chmod u+rwx *filename*

```

hope that helps

atreju

---

### Post by Mobus on 2007-09-26
Ok, I am getting the same error, however I AM able to make the folder myself.  When I make the folder myself it shows up in the file browser, but it still gives the same error message when I try to click on the trash.  I am also using KDE.

---

### Post by Mobus on 2007-09-26
FIXED

I chmoded the folder I created and it opened.

---

