---
title: "users-admin issue"
date: 2011-11-21
forum: Desktop Environments
---

### Post by lucacerone on 2011-11-21
Dear all,
after the upgrade I had some issues with Gnome and Unity so following
the advice of one user on the forum I have created a new account luca2
and copied all the hidden files and directories into the home folder of my main user luca.
This actually solved the issue, but now I'm experiencing some trouble when using the users-admin program.
Whenever I lunch the command I can get the gui and see the list of users
but I can't modify anything. When I press the various "change" buttons nothing happens.

If I login with the luca2 user I don't have this issue, so I think it might probably depend on the fact that some of the files I have copied are specific for the luca2 user (maybe thwy give permission based on the uid or something like that?)

Can you please give me an advice on how to solve this issue?
So far replacing my config files with the ones of a different user only seemed to have caused this issue (although I haven't tested the system long enough).

Thanks in advance for your help,
Cheers, -Luca

---

### Post by jimmydean886-2 on 2011-11-21
Try getting rid of the config files pertaining to the program that are hidden in your home directory. Press <ctrl>+<h> to show them, then just either search through the loose files, or sometimes the config is in ./.config or./.local.
Getting rid of that usually solves issues of that type for me, usually caused by a bad file somewhere.

---

### Post by grahammechanical on 2011-11-21
You seem to be saying that you have administration rights as luca2 but not as luca. Correct? Is it possible to be luca2 and give administration rights to the user luca? Will that solve this problem?

You most definitely want to have one user with administration rights. So be careful if you delete users.

Regards.

---

### Post by lucacerone on 2011-11-22
Hi guys thanks for the help.
grahammechanical I didn't want to assign the permission of user luca2 to luca because I want to delete luca2 when I've tested that everything is working. Thanks jimmydean and I didn't know that the
permission files are in .config and .local (I'll try to have a look at them).

In any case it seems that I could solve the issue by issuing:
```
sudo dpkg --configure -a
``` from a terminal.
I haven't experienced anything strange after,
I just wait a couple of days for testing and will mark the thread as solved.

Anyhow, I haven't really understood what this command does 
(I think it has reconfigured the settings of all the installed packages???)

Thanks for your help,
luca

---

