---
title: "Where Kate is installed?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by fyss on 2006-03-09
This is the first question of an ubuntu newbie.Right now I installed the KDE editor 
Kate through package manager&#12290;But now I cant find it now. Anyone call tell me usually where the package manager install a utility?Thanks a lot!

---

### Post by dcstar on 2006-03-09
[QUOTE=fyss]This is the first question of an ubuntu newbie.Right now I installed the KDE editor 
Kate through package manager&#12290;But now I cant find it now. Anyone call tell me usually where the package manager install a utility?Thanks a lot![/QUOTE]
Open a terminal:

"whereis kate"
"locate kate"

---

### Post by fyss on 2006-03-09
It seems that the terminal doesnt want to give me some answer.
I typed "whereis Kate"
It answered "Kate:"
At least it should give me some path to Kate

---

### Post by sdide on 2006-03-09
the command is kate, (small "k")
You have atleast 3 options locate, whereis and which

$ locate kate
Should give you a lot of garble, among all that - what you are looking for.
$ whereis kate 
kate: /usr/bin/kate /usr/bin/X11/kate /usr/share/man/man1/kate.1.gz
If that answers just: kate:, it means kate is not installed properly
$ which kate
/usr/bin/kate

.

---

### Post by fyss on 2006-03-09
Thank you!
I've got it!

---

