---
title: "Can't find Desktop Sharing in Ubuntu 14.04"
date: 2014-08-14
forum: Desktop Environments
---

### Post by griffith12345 on 2014-08-14
I have read everywhere that to enable a VNC server, I go to Settings > Destop Sharing, but I can't find it.  The software center says it is installed but it doesn't show up. If I do gsettings list-recursively org.gnome.Vino, I get back about 15 results.

Any hints appreciated.
Thanks,
-- John

---

### Post by deadflowr on 2014-08-15
Did you simply searched the dash menu?
Click on the windows key button on your keyboard(also known as the meta key or super key) and type "sharing".
The first or second entry should be Desktop Sharing.

Or simply open a terminal and type
vino-preferences

---

### Post by griffith12345 on 2014-08-15
I searched for 'vino' and 'vnc' in the searchbox I get when I, for instance, hi tthe windows key. For 'vino' I get nothing. For 'vnc' I get Vinagre and Remmina, neither of which appear to be servers. Searching for 'sharing' only gives me Personal File Sharing.

I looked in 'Show Applications' and didn't find desktop sharing or vino.

I looked in the system settings and do not find desktop sharing.

With dconf editor, there is nothing under desktop > gnome other than crypto. Other web pages have indicated that I should find 'remote-access' under there.

Desktop sharing/vino seems to be hidden for some reason. Is there a command line way to launch the GUI or run it?

Thanks,
-- John

---

### Post by griffith12345 on 2014-08-15
Ah, I tried typing 'vino' in a terminal and got nothing and no hints, but 'vino-preferences' works!

Still confused why it doesn't show up in other places ... but willing to leave well-enough alone

Thanks!

---

### Post by deadflowr on 2014-08-15
I don't know.
If I run a quick search for sharing, desktop, or desktop sharing, it gets listed.
Basically, though, vino-preferences is the actual program launcher command, so if that works it works.

Also, yes remmina is not a server, but rather the client you can use to access the server.

As well, if you think you've found the solution that works for you please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), in the hopes that others might be able to use what you have figured out.

---

### Post by griffith12345 on 2014-08-15
Thanks for your help - and the hints on how to close this thread. -- John

---

