---
title: "Ubuntu 9.04:  Tracker Applet Errors"
date: 2009-05-01
forum: General Help
---

### Post by tinker123 on 2009-05-01
I just upgraded to Ubuntu 9.04.

I keep getting a pop-up from the Tracker Applet that reads:

> 
Tracker
There was an error while performing indexing
Index corrupted.



If I press the "okay" or "cancel" button the pop-up keeps coming back.  If I press the "reindex" button the pop-up will go away, but will come back when I reboot.

Any idea how to fix this or make the pop-up stay gone away?

Thanks in advance

---

### Post by Turbo825 on 2009-05-02
I just upgraded to 9.04 and have the same issue. Anybody got any ideas how to fix this or why it happens?

---

### Post by holodila on 2009-05-02
I just forcefully kill this window and enjoy a working system =)

---

### Post by stepanstas on 2009-05-02
Force kill works but is not a solution.

Same issue here.

So far since upgrade I have been getting 4 major issues which everyone else seems to be getting.  I'm starting to wonder why they keep this 6 months upgrade commitment.  Each upgrade new issues come up.

---

### Post by tinker123 on 2009-05-02
This *may* help
[http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption](http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption)

---

### Post by stepanstas on 2009-05-02
Thanks for the link, solution sounds like it will work but for me it doesn't.  If i follow the instructions it will say "Could not open location 'file:///home/[username]/tracker-processes%20-r'"
> If i run in terminal it says, "
The program 'tracker-processes' is currently not installed.  You can install it by typing:
sudo apt-get install tracker-utils
bash: tracker-processes: command not found

At least they are working on it.

---

### Post by tinker123 on 2009-05-03
Their workaround at the URL worked or at least that error pop-up went away permanently.

---

### Post by y10linux on 2009-05-04
> **stepanstas said:**
> Thanks for the link, solution sounds like it will work but for me it doesn't.  If i follow the instructions it will say "Could not open location 'file:///home/[username]/tracker-processes%20-r'"


At least they are working on it.


You need to install the program first, so to solve it:

$ sudo apt-get install tracker-utils

and then you can execute

$ tracker-processes -r

I have tried it and it seems to work fine now.

---

### Post by JimBuntu on 2009-05-08
just did it on my machine. All seemed to go well. Is this something I only have to do once? Or am I going to have to do this every time my computer is restarted?

---

