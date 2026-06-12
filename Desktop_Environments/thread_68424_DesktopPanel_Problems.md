---
title: "Desktop/Panel Problems"
date: 2005-09-23
forum: Desktop Environments
---

### Post by RikoW on 2005-09-23
Hi all,

since a few days, I have the problem that certain panel applets die on start-up:

Workspace Switcher
Show Desktop
Window List

The message box tells me that they died unexpectedly and if I want to reload. Reload works flawless. So, it's not a big deal but a bit annoying. I already removed them from the panel and added again, but didn't make a difference.

It seems to have conincided with the last Ubuntu update, which was (according to the  synaptic history):

```
Commit Log for Tue Sep 20 08:47:47 2005


Upgraded the following packages:
bsdutils (1:2.12p-2ubuntu2) to 1:2.12p-2ubuntu2.2
mount (2.12p-2ubuntu2) to 2.12p-2ubuntu2.2
util-linux (2.12p-2ubuntu2) to 2.12p-2ubuntu2.2

```

Anybody has any hints of what's might be the problem?

Thanks,

             Riko

---

### Post by Hairy_Palms on 2005-09-23
i dont have a solution but i have exactly the same problem, and it doesnt happen every time just sometimes so its nothing major but it might need to be reported to bugzilla if someone can make it recreatable

---

### Post by lisje on 2005-09-23
I had the same problem after installing an extra applet for my gnome-panel... I just uninstalled the applet I had installed and reïnstalled the gnome-applets + the data.. and problem solved :-)

---

### Post by RikoW on 2005-09-23
hmm, I didn't install any new applets for a long time, so I doubt it has something to with that.

But maybe reinstalling the gnome-applets will do the trick ...
will try it on the weekend.

BTW. It seems to always happen to me, not just occasionally

---

### Post by Dooglus on 2005-09-23
One thing that's always worth trying when your GNOME desktop starts playing up is to make a new user account, log in as that user, and add stuff to that user's panels just like in yours.

If it works fine for the new user then something has got corrupted in one of your ~/.gnome* directories.  The only solution I've found is to delete them and start building my panels again from scratch.  If the new user has the same problem as your original user then it's more likely to be a global problem.

I've had do delete my .gnome* directories a couple of times in the past when they've stopped working.  Perhaps there's a better solution.  If so, perhaps someone will let us know.

---

### Post by RikoW on 2005-09-25
Indeed!!

I deleted my panel by accident the other day. After adding it again and adding the above applets, they don't seem to crash anymore.
Note, that removing the applets and adding them (without removing the entire panel) did NOT do the trick.

Thanks,

              Riko

---

### Post by Irony on 2005-09-27
Same problem here, I get;

Workspace Switcher
Show Desktop
Window List

has quit unexpectedly.

My Synaptic History;

Commit Log for Mon Sep 26 21:51:55 2005

Upgraded the following packages:
mount (2.12p-2ubuntu2) to 2.12p-2ubuntu2.2
util-linux (2.12p-2ubuntu2) to 2.12p-2ubuntu2.2

Commit Log for Sun Sep 25 20:03:20 2005

Upgraded the following packages:
bsdutils (1:2.12p-2ubuntu2) to 1:2.12p-2ubuntu2.2
libmysqlclient12 (4.0.23-3ubuntu2) to 4.0.23-3ubuntu2.1
libnspr4 (2:1.7.10-0ubuntu05.04) to 2:1.7.12-0ubuntu05.04
libnss3 (2:1.7.10-0ubuntu05.04) to 2:1.7.12-0ubuntu05.04
mysql-common (4.0.23-3ubuntu2) to 4.0.23-3ubuntu2.1

I'll try deleting the panels and putting them back.

---

### Post by Irony on 2005-09-27
If I accidently deleted both panels how would I add them back.

I made a point of deleting one panel then using the other panel to add a panel.

---

### Post by lisje on 2005-09-27
[QUOTE=Irony]If I accidently deleted both panels how would I add them back.

I made a point of deleting one panel then using the other panel to add a panel.[/QUOTE]
you just press Alt+F2 to get that "run application" thingie and type xterm.. to get commandline open .. then launch gnome-panel ... you'll get at least one panel running.
At least that worked when I accedentally deleted my gnome-panel

then I fiddled something with sessions and stuff so it would accidentally launch twice and then deleted one of those two...

---

### Post by Irony on 2005-09-27
What do you actually type at the command line?

---

### Post by mcduck on 2005-09-27
[QUOTE=Irony]What do you actually type at the command line?[/QUOTE]
'gnome-panel'

---

### Post by Irony on 2005-09-28
The deleting of panels and reinstating them seems to have worked, ubuntu started up today without fault.

---

