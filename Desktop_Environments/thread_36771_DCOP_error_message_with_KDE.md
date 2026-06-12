---
title: "DCOP error message with KDE"
date: 2005-05-24
forum: Desktop Environments
---

### Post by ggore on 2005-05-24
I installed KDE using Synaptic on my Ubuntu box.  When I try to start KDE I receive an error message that the ,kde directory is not writable, something having to do with DCOP server, and then KDE dies, it will not load at all.  

When I browse my Home directory in Gnome, I find that the .kde directory is locked and has a red X.  I assume it thinks it is owned by Root, not me as the only user of the computer.  How do I change this so that it is writable for me as the regular user?  My guess is to somehow use a "sudo chown" command to change ownership.   What is the correct command and syntax?  Thanks.

---

### Post by JonahRowley on 2005-05-24
I think **sudo chown -R jonah:jonah ~/.kde** is what you're looking for.  Though, if .kde is owned by root, then it's probably not anything meaningful, so you could also **rm -Rf ~/.kde**.  Look for other files owned by root in your home directory and clean them up as well.  **find ~ ! -user jonah** will list them for you.

---

