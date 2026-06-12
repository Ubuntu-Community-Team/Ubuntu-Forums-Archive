---
title: "Beryl Problems in Edgy"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by RelativelyQuantum on 2007-06-17
Hi all.

I'm having trouble installing Beryl in my newly installed Edgy (I installed it again after a few unfortunate happenings in Feisty). When I open the "Add/Remove Programs" app, searching for Beryl yields no results.

Anyone have any thoughts?

I'll try Synaptic just in case, but any insight would be appreciated.

---

### Post by RelativelyQuantum on 2007-06-17
I've rebooted my machine and checked Synaptic, but got nowhere with that. I'll try running it as a command in Terminal, and post the results on this thread.

Any advice would help...

---

### Post by RelativelyQuantum on 2007-06-17
I've gotten varying results on the forum, but it seems I can't install Beryl in Edgy :(. I installed Compiz instead; now I just need to figure out how to configure it.

---

### Post by zero244 on 2007-06-17
Open your sources list with the command below and add the deb line to the list and save it.
Then open Synaptic and reload the list.
Then do a search for beryl
And version 0.2.0 and support files should come up.
Just select install it and logout and back in and beryl will show up under your menu list under system tools.

gksu gedit /etc/apt/sources.list

# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by RelativelyQuantum on 2007-06-17
> **zero244 said:**
> # deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

Are you joking? Have you seen that link??

In any case, where do I place the deb line in the file? I have it opened, but am not sure where to go from here...

---

### Post by RelativelyQuantum on 2007-06-17
Oh, ok - I think I've got it.

Sorry about that!

(Really, though - Have you seen the link? :))

---

### Post by RelativelyQuantum on 2007-06-17
Ok, I added the deb line...and nothing new happened. Is there anything I'm missing?

---

### Post by RelativelyQuantum on 2007-06-17
```
$ gksu gedit /etc/apt/sources.list
(gedit:4907): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

The window still came up, but what does this mean?

---

