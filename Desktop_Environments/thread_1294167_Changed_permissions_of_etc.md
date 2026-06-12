---
title: "Changed permissions of /etc/"
date: 2009-10-18
forum: Desktop Environments
---

### Post by varunbhatbm on 2009-10-18
Hi,
I changed permissions of /etc directory with this command, 
"sudo chmod 777 -R /etc"

Now I'm unable to access synaptic, janitor and install updates.

Please tell me how do I correct this problem.

---

### Post by 3rdalbum on 2009-10-18
My god, what caused you to do that?

I think realistically the quickest solution might be to reinstall Ubuntu.

Do any sudo operations work? For instance:

```
sudo whoami
```

Does it return "root", or an error message?

---

### Post by Drood on 2009-10-18
Is it possible to just change them back to yourself ? If not, can't you boot into a live cd and then change them to yourself ? sudo chmod -R +rw /etc . Wouldn't that give everyone read and write permissions , so when you boot back into normal ubuntu you would have permissions.

---

### Post by Lars Noodén on 2009-10-20
I just checked a bare-bones installation of jaunty and find that there are close to three thousand files and directories.  There are probably more if you have installed extra packages.  

The safe way might to boot to  the rescue CD and back up the home directory and any other data you want to keep.  Then try a fresh install.  If you don't have a separate /home partition, now is the time to add one.  

I've [attached](http://ubuntuforums.org/attachment.php?attachmentid=132521&d=1256059614) the output from a survey of the permissions from /etc gathered using the script:

[INDENT][FONT="Courier New"]sudo find /etc -exec stat --printf="chmod %a %n;\n   chown %u:%g %n;\n" {} \;[/FONT][/INDENT]

---

