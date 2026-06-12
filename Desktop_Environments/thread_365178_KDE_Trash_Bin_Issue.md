---
title: "KDE Trash Bin Issue"
date: 2007-02-19
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-02-19
Hey everyone,

I'm having a weird problem with Kubuntu (KDE). Every time I delete something I can empty the trash bin. However, as soon as I delete another item I'm unable to empty the trash bin. I.e., the "Empty Trash Bin" option is grayed out. It's fixed as soon as I reboot but I'm back to square one when I delete more items.

Has anyone experienced this problem and know of a possible fix/workaround?

---

### Post by chggr on 2007-02-19
The Trash is actually a secret folder inside your home folder named ".Trash". The fact that its name begins with a dot, makes this folder hidden and normally you can't see it (It doesn't appear inside your home folder). 

So, what you can do is delete the files using the command line. Open a Konsole and type:

sudo rm /home/<YOUR USERNAME>/.Trash/*

Where you will replace <YOUR USERNAME> with your actual user name.
Normally ALL the contents of the Trash will be cleared (regular files, files you dont have permission to write on, hidden files etc), and that should fix the problem. Tell us if this works...

---

