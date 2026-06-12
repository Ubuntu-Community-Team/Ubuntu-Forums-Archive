---
title: "Effect of using sudo sudo"
date: 2009-05-27
forum: General Help
---

### Post by sandy8925 on 2009-05-27
I just wanted to know what would happen if I used some command like:

sudo sudo <command>

Would it work as normal or create any side effects ?]

Also if I put some terminal commands in a file say cmds and run it as:

sudo ./cmds

will all the commands in the file then run with root permission ?

---

### Post by Boondoklife on 2009-05-27
> **sandy8925 said:**
> I just wanted to know what would happen if I used some command like:

sudo sudo <command>

Would it work as normal or create any side effects ?]

Also if I put some terminal commands in a file say cmds and run it as:

sudo ./cmds

will all the commands in the file then run with root permission ?

Double sudo should not really matter, it is kinda like root running sudo then the command, redundant.

as far as the sudo to run the script, all actions in it should be run with elevated rights.

---

### Post by sandy8925 on 2009-05-28
ok. thanks !

---

