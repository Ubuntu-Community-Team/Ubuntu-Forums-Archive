---
title: "can't start gnome / failsafe gnome starts"
date: 2005-08-09
forum: Desktop Environments
---

### Post by Lambert on 2005-08-09
Where do I start to trouble shoot gnome not starting? I've installed ubuntu no hitches but when I try to log into gnome it says can't start session and goes into fail safe xterm. i log out and try fail safe gnome and it starts ok.

---

### Post by varunus on 2005-08-09
Can you log into failsafe, open a terminal (applications->system tools->terminal) and type the following:

cd /home
ls -l
cd ~
ls -lA
cd .gnome2
ls -lA

---

### Post by Lambert on 2005-08-09
[QUOTE=varunus]Can you log into failsafe, open a terminal (applications->system tools->terminal) and type the following:

cd /home
ls -l
cd ~
ls -lA
cd .gnome2
ls -lA[/QUOTE]

Yes I can, do you want me to post output here?

Part of my goal is not to just solve this but to understand and learn a little about linux  and how to troubleshoot a problem. These show file permissions which I did set up login as root and tried and got the same results if that matters.

---

### Post by varunus on 2005-08-09
Well, an explanation of why I would like you to post those here:

GNOME can sometimes mess up if the home directory of the user who tries to log in becomes owned by another user.  Enabling the root account (as you seem to have done) can cause this problem sometimes.  You should look at the output and make sure that your user owns all of the files listed.  Just in case, you could always try a

chown -R yourusername .gnome2

chown changes the owner of a file.  R means recursive, which will tackle every file and subdirectory within the .gnome2 folder along with the folder itself.

---

