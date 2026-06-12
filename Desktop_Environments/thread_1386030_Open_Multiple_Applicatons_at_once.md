---
title: "Open Multiple Applicatons at once"
date: 2010-01-20
forum: Desktop Environments
---

### Post by JockMcJock on 2010-01-20
Hi, I am a new Ubuntu user. I have set up 3 desk spaces. One for Internet, one for study and one for admin. Is there a way that I can have one icon that would open all the desired programs on each desktop, eg I would have an icon on my admin desktop that would open my 3 spreadsheet files 3 word processor files and a finance program all at once?

Any help would be appreciated.

Best,
       JockMcJock

---

### Post by doas777 on 2010-01-20
well, you can create a script, and link it to a launcher. the script would run each of the commands to open each of your apps.

---

### Post by JockMcJock on 2010-01-20
Can you tell me how to do this or point me in the right direction?

Thanks.

---

### Post by Rhubarb on 2010-01-20
Make up a text file, put in the applications you wish to execute, save it, then make that text file executable:-

test.sh
```
#!/bin/bash
oocalc ~/Documents/test.ods &&
oowriter ~/Documents/test.odt &&
exit 0
```

To make it executable:
```
chmod +x test.sh
```

You'll find that the applications you wish to be opened will be opened in the current desktop, so you may need a few scripts to be run for each desktop.
If you wish to be really smart, and have one executable script open up all your applications and have them in the correct workspaces (desktops), then you'll probably need to use devilspie.
[Here]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/") is a good brief tutorial about devilspie

I haven't had much of a chance to verify all this, as I've only briefly used devilspie before.  But, essentially devilspie allows you to automatically detect newly opened windows, and do something with them, such as move them to a different desktop / maximise / re-size them.

---

### Post by M1GEO on 2010-01-20
You may also need to the application with the desktop you would like the program on.  Extending test.sh from *Rhubarb*:

```

#!/bin/bash
oocalc --display=:0.0 ~/Documents/test.ods &&
oowriter --display=:0.1 ~/Documents/test.odt &&
exit 0

```

the first display corresponds to --display=:0.0, the second to --display=:0.1, so in the above example, you will get a spreadsheet on your first screen, and a document on the second screen.

Most applications support this, but not all of them do.  You may also find the $DISPLAY variable useful too.  See [thread 1386390]("http://ubuntuforums.org/showthread.php?t=1386390") for a better explanation.

Hope this helped :)

---

### Post by JockMcJock on 2010-01-21
Hi, thanks for the help guys.


Could you tell me exactly to make a file executable?

---

### Post by doas777 on 2010-01-21
> **JockMcJock said:**
> Hi, thanks for the help guys.


Could you tell me exactly to make a file executable?

you can rightclick -> properties -> Permissions and check the box that says "Allow executing file as program".

or just use 'chmod u+x <path to file>' at the terminal.

---

