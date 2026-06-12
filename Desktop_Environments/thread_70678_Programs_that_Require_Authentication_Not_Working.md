---
title: "Programs that Require Authentication Not Working"
date: 2005-09-30
forum: Desktop Environments
---

### Post by Prog on 2005-09-30
I work for residential life at Louisiana State University, and I brought up the idea of installing Linux on the E-Mail stations inside of the dorms...so we'd never have to worry about the E-Mail stations ever again. :p 

Anyway, my boss told me I could try it out on a computer to see how it worked, so I did.  Here's what happened...

I skipped network installation and when it got to booting into Gnome, it said that it couldn't contact the network address associated with -name of the computer- blah blah, and I could ignore or try again.

Welllllll, pressing ignore allowed me to get into Gnome, but then nothing that requires authentication to open would load.  For example, a root terminal.  The icon for it comes up on the bottom panel, I get a waiting mouse pointer, and then the icon in the panel goes away and nothing happens.  I've tried restarting, and nothing.  I've never run into this problem before on any of my Hoary installations on one of my computers, so I'm clueless.  

I really don't want to have to pass up the opportunity to further spread Linux to a more mainstream audience, or at least, I'd like to relieve that audience of the pain of Windows 2000, so any help would be much appreciated. ;)

---

### Post by adwait on 2005-09-30
Umm.....maybe some problem with gksudo? Try reinstlaling it with
```

sudo apt-get install gksudo -f

```

Just a guess..........

---

### Post by Prog on 2005-09-30
I don't have access to the computer until Monday night, so thanks for the suggestion and please keep on suggesting!

---

### Post by tehwa on 2005-09-30
I replied to a thread about 10 minutes ago suggesting this same solution, and I hate to look like an old dog with a new trick....```
sudo gedit /etc/hosts
```
make sure that the format resembles this:```
127.0.0.1 localhost.localdomain localhost moog
```where my computer is named "moog", replace with the hostname of your coputer.

---

