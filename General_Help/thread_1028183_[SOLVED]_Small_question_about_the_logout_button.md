---
title: "[SOLVED] Small question about the logout button"
date: 2009-01-02
forum: General Help
---

### Post by spcwingo on 2009-01-02
Hello all.  I have a quick question about the logout button in Gnome.  When this button is pressed, what is executed (app/full path) to bring up the logout prompt?  I would just like to know so I can add a logout button to wbar.  Thanks in advance.

PS: I tried searching the forum first for an answer, but to no avail this time.  So, I apologize in advance if this is another dead horse thread.

---

### Post by ajcham on 2009-01-02
```
/usr/bin/gnome-session-save --logout-dialog

```

---

### Post by spcwingo on 2009-01-02
Thanks for your reply.  I input that command in my .wbar file, but it doesn't work.  To see if there were any errors I ran that same command in a terminal and here is the output:

```
jonathan@jonathans:~$ gnome-session-save --logout-dialog
Unknown option --logout-dialog
Run 'gnome-session-save --help' to see a full list of available command line options.

```

Any other suggestions?

---

### Post by ajcham on 2009-01-02
> **spcwingo said:**
> Thanks for your reply.  I input that command in my .wbar file, but it doesn't work.  To see if there were any errors I ran that same command in a terminal and here is the output:

```
jonathan@jonathans:~$ gnome-session-save --logout-dialog
Unknown option --logout-dialog
Run 'gnome-session-save --help' to see a full list of available command line options.

```

Any other suggestions?

Which version of Ubuntu are you running?  I'm on Intrepid, and the command is definitely the one I gave you. Have you tried ```
gnome-session-save --help
``` as suggested, to see the available options?

In any case, if you aren't bothered about bringing up the dialog, you could use ```
gnome-session-save --logout
``` or ```
gnome-session-save --force-logout
``` to log out directly (assuming that they are available as options - run the help command above to make sure).

---

### Post by spcwingo on 2009-01-02
I figured it out.\\:D/  It's:

```
gnome-session-save --kill
```

Thanks, ajcham.  You put me on the right track.  I would have never have figured it out without your suggestion.  Thanks again!  BTW, I'm still on Hardy and the --kill switch brings up the dialog (that's what I was after).

---

