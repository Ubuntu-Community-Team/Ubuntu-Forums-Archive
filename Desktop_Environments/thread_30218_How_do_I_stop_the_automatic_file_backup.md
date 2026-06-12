---
title: "How do I stop the automatic file backup?"
date: 2005-04-27
forum: Desktop Environments
---

### Post by ryanrad on 2005-04-27
Hello everyone, there's probably a very simple solution to this, but I can't find it and it's driving me nuts.  

Everytime I edit a file, Ubuntu/Gnome creates a backup with a tilde at the end.  Is there any way to make it stop?

file.txt
file.txt~

My entire home directory is riddled with these things.

---

### Post by ryanrad on 2005-04-27
Nevermind, I'm a complete idiot.  I just realized that maybe gedit was doing it.  I was right, somehow the check box got checked to automatically create a backup before saving.

---

### Post by bored2k on 2005-04-27
1. Edit > Preferences > PLugins > Uncheck save a copy
2. Edit > Preferences > Editor > Uncheck create a backup
3. Panel > System Tools > Configuration editor > apps > gedit-2 > save > uncheck create backup

---

### Post by bored2k on 2005-04-27
[QUOTE=ryanrad]Nevermind, I'm a complete idiot.  I just realized that maybe gedit was doing it.  I was right, somehow the check box got checked to automatically create a backup before saving.[/QUOTE]
 It's on by default. It's actually a nice feature. You don't even see the hidden ~ files [at least I don't]. Excellent for scripts, in case one screws up.

---

### Post by tread on 2005-04-27
Tell me about it! I once lost an entire days work because of a script gone awry ... and didn't have those nice ~ backups ..  :-(

---

### Post by bored2k on 2005-04-27
[QUOTE=tread]Tell me about it! I once lost an entire days work because of a script gone awry ... and didn't have those nice ~ backups ..  :-([/QUOTE]
 Most of the nix editors have this feature, and it's not because its bad ;) [I love nano for this, and joe <-- though it has another backup name, not ~].

---

### Post by ryanrad on 2005-04-28
Thanks everyone.

It wouldn't be so bad, except that I see all of them even when I have nautilus unchecked so that it does not show hidden files.

I'm a recent convert to Linux.  Maybe I'll turn it back on and see if I get used to it.

---

