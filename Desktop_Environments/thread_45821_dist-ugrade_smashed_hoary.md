---
title: "dist-ugrade smashed hoary"
date: 2005-07-01
forum: Desktop Environments
---

### Post by monkman on 2005-07-01
i did an dist-upgrade, which failed somewhere updateing a python-thing. i rebooted the system. the kde login starts, but i can't login anymore. the are no mouse drivers loaded, so that i eventuelly could switch to a console or do an init 3 or something.

there are some errors during booting, something with the find command. the resolving of ubuntclock.org doesn't work either. as the mouse doesn't work, i suppose no driver is loaded to handle my networkcard. the nvidia driver is loaded.

what can i do now? is there any rescue option on the install cd? recovery kernel doesn't help. imho the kernel wasn't touched by the update. it's more the systemconfiguration, which seems to be messed up.


THANX for any help

---

### Post by dfghost on 2005-07-01
carefull with that, first of all, backup everything before ever trying an expirimental version or any version for that matter.  The only thing i can tell ya is reload.  Think twice and backup once before ya try it again.  Sorry bout the bad news, but it seems like you corrupted your system.  

BACKUP backup and backup, ya just can't say it enough times.

---

### Post by monkman on 2005-07-02
so i suppose, i had too much stuff in my sources.list.
now i will backup some files from home/USER and reinstall ubuntu....

how can i prevent such things in the future?

"simply" backup / ?

THANX anyway

---

### Post by t2kburl on 2005-07-02
i put my /home on a seperate partition. That way whenever I have to reload /  my /home stays untouched.

---

### Post by dfghost on 2005-07-04
hey, that's a good idea.  And you don't have to keep all of the root directory backed-up.  Just non-recoverables like cgi files or html's that you made, stuff like that.  Also, whenever you edit anytype of file, especially system files, backitup first.  Try putting it in a remote location, meaning off of the server, and also do

sudo cp /directory/filename /directory/filename.bak

that way, you have another backup right in the directory that you're working with.  Make sense?

---

### Post by f1dave on 2005-07-05
Have packages actually ruined or broken dependencies or anything?

You could always try apt-get -f dist-upgrade or apt-get -f install i suppose.

---

