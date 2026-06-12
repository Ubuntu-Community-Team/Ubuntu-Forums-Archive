---
title: "Your session only lasted 10 seconds...."
date: 2006-09-20
forum: Desktop Environments
---

### Post by Mikekie_noob on 2006-09-20
Hi. I made a dumb mistake by adding a PATH statement to /etc/enviroment file (was installing Oracle 10g and followed bad instructions...).  I cannot get into X session.  If I go to Failsafe Gnome it hangs and never loads.  If I Failsafe Terminal it does not recognize any commands.

How can I get the Failsafe Terminal to recognize commands so I can edit the /etc/environment file to delete bad PATH statement?

Any help will be much appreciated... be gentle I am a noob..

---

### Post by kick6 on 2006-09-20
This is kinda ghetto, but if you hit ctrl+alt+backspace enough times GDM will eventually give up, and drop you to a text-only login prompt.  From there you should be able to edit the file.  Aftewards run "startx" from the prompt to bring back your gui.

---

### Post by RoyArne on 2006-09-20
> **Mikekie_noob said:**
> Hi. I made a dumb mistake by adding a PATH statement to /etc/enviroment file ... If I Failsafe Terminal it does not recognize any commands.

How can I get the Failsafe Terminal to recognize commands so I can edit the /etc/environment file to delete bad PATH statement?


Press **Ctrl+Alt+F1** to get to a console window and log in.

You can set your path temporarily at the command line:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
```
and type
```
sudo nano /etc/environment
```

to edit your file.

---

### Post by Mikekie_noob on 2006-09-20
Thanks for quick reply kick6!  I can get into the Terminal but then I get these errors:

bash: [: = : unary operator expected
bash: [:     to many arguments
bash: sed: command not found

It still does not let me run say vi to edit the /etc/environment file.  I get a command not found error.  I tried running vi directly from /bin (where vi is stored in most distros) and it says it cannot find vi.

Stumped at this moment.

---

### Post by kick6 on 2006-09-20
did you login as root or as a user?  Try exporting your path first as suggested by RoyArne

---

### Post by Mikekie_noob on 2006-09-20
Thanks RoyArne!  That did it.  Issue closed.

---

