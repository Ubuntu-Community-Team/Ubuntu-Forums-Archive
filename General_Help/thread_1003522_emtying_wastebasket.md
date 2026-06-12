---
title: "emtying wastebasket"
date: 2008-12-06
forum: General Help
---

### Post by gandalf458 on 2008-12-06
I have a folder in my wastebasket which I can't get rid of. If I try to delete it I get an error message telling me there was an "Error while deleting".
Any ideas please guys?

---

### Post by Elfy on 2008-12-06
Might need root rights to delete it - possibly

This thread should help - [http://ohioloco.ubuntuforums.org/showthread.php?t=898573](http://ohioloco.ubuntuforums.org/showthread.php?t=898573)

---

### Post by gandalf458 on 2008-12-06
Thanks for the link. I'm having trouble locating Trash using Nautilus though. I'm not sure how to navigate to ~/.local/share/Trash

---

### Post by Arup on 2008-12-06
Easy and effective way.

sudo apt-get install trash-cli

sudo su
empty trash

All your root trash is gone.

---

### Post by Elfy on 2008-12-06
~/.local/share/Trash - ~/ is shorthand for your /home folder - to see hidden files use Ctrl+H

---

### Post by lukjad on 2008-12-06
I think that the trouble is that sometimes in Hardy, you can't just delete certain files easily. Here is a command I use to force the deletion of all the files in the home trash:
Go to Applications->Accessories->Terminal and type:

```
sudo rm -r ~/.local/share/Trash/files/
```

This should do it!

---

### Post by gandalf458 on 2008-12-06
Thanks guys.

---

### Post by lukjad on 2008-12-06
Anytime. :D

---

