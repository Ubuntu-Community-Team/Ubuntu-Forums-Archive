---
title: "Evolution completely died!"
date: 2005-02-14
forum: Desktop Environments
---

### Post by v79 on 2005-02-14
I really don't know what I've done here. Booted up into Ubuntu, and Evolution has crashed. It doesn't find any of my mail folders (the tree view only holds VFolders), the UI is unresponsive and doesn't draw. Can't click anywhere, can't do anything with them.

Ok, so I copied the .evolution/mail/local folder to a safe location, uninstalled and reinstalled evolution. No effect. I moved the entire .evolution folder out of /home/, so in theory Evo would just think it's a fresh install. But nothing changed! No startup wizard, just the same frozen interface with no mail folders listed!

The only hint I have is this line:

$ evolution

(evolution:5541): evolution-smime-WARNING **: initializing security library without cert databases.

Help me please!

ljd

---

### Post by nocturn on 2005-02-14
Try evolution --force-shutdown 
Then evolution again.

---

### Post by v79 on 2005-02-14
Thanks, that got evolution up and running again. Now can I just copy the contents of local/ back into .evolution/mail/local again to get all my messages back? Are there any files I don't need (index files, for instance?).

Thanks again

---

### Post by v79 on 2005-02-14
Answered my own question - copied the files, and all was well. Couple of settings lost, but nothing major. Panic over!

---

