---
title: "Gnome Terminal Tab Completion"
date: 2008-05-14
forum: Desktop Environments
---

### Post by boscopup on 2008-05-14
I did a search in the forums, and found others mention this problem, but when I tried the fix, it didn't change anything. :confused:

I just installed Ubuntu 8.04 yesterday, using the FakeRaidHowto instructions, although I didn't realize until after I'd installed almost everything that I probably could have double clicked the install button and done the "normal" method of installing instead of using debootstrap. But I did a debootstrap installation, including unbuntu-desktop and all that fun stuff, and everything seems to be working except my Gnome Terminal tab completion. I NEED tab completion. So used to it that I can't live without it.

What I've tried:
1) Current Profile->Title And Command... checked "Run command as a login shell"
2) Edited /etc/bash.bashrc and uncommented the lines about tab completion.

I've rebooted since doing these things, so if it's using that bashrc file, it *should* have gotten the change. I suspect it may not be using it at all.

I'm a bit rusty on the shell stuff, so help would be much appreciated. :)

---

### Post by prshah on 2008-05-14
> **boscopup said:**
> 
2) Edited /etc/bash.bashrc and uncommented the lines about tab completion.


Did you also check your ".bashrc" in your home directory? If you change that, there's no need to reboot; just close any open Terminals, and open a new one, the change should be immediate.

---

### Post by boscopup on 2008-05-14
I don't have a .bashrc in my home directory (I did 'ls -a' and also did a search, just in case it gets stuck in a directory somewhere). I just tried copying /etc/bash.bashrc to .bashrc in my home directory, closed that terminal and opened a new one, and still no tab completion.

I'm wondering if maybe my shell isn't using bash? How would I change that? :confused:

echo $SHELL results in /bin/sh

---

### Post by boscopup on 2008-05-15
Ok, I got it fixed. I edited /etc/passwd and changed the shell for my username from /bin/sh to /bin/bash. I had to exit Gnome in order for it to take effect.

Ah... much better. :)

---

