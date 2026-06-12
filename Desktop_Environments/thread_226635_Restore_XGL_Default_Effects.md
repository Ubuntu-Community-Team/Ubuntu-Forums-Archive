---
title: "Restore XGL Default Effects"
date: 2006-07-31
forum: Desktop Environments
---

### Post by kalpik on 2006-07-31
Hi everyone!

I basically got XGL working on my machine. Everything was fine untill i started to fool around with gset-compiz.. I've messed some settings (wobbly most probably.. And now my tooltips and menus dont have the wobbly effect. Is there any way i can just restore the settings of *all* the plugins to their respective defaults as they were when i first installed XGL?

Thanks in advance!

---

### Post by cptnapalm on 2006-07-31
I'm at work, so I'm basically guessing, but perhaps may help.

ls /home/yourusername/.compiz

if it only spits back the name, then it is a file and open it with a text editor, or possibly just delete it.

if it lists contents, then it is a directory.  Head inside and find configuration files or just rm -R it.

Again, this is a blind guess, but it *could* be right.

---

### Post by kalpik on 2006-07-31
Hi!

Thanks for your reply. I already tried that! It just contains the data (png+ini) for the compiz themes, nothing else :(

---

