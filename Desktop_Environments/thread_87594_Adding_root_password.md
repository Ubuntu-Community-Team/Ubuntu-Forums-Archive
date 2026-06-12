---
title: "Adding root password"
date: 2005-11-08
forum: Desktop Environments
---

### Post by bobes on 2005-11-08
I add the root password to system. Now not working any apps which requiring root privilege. Which step I must do to system work correctly ???

Thanks, Bob

---

### Post by earobinson on 2005-11-08
im not sure I understand you question

how did you add the root password?

how dont the apps work? Is the password not accecpted?

Just because you changed your root password still when you do a sudo you must use the current users password

---

### Post by bobes on 2005-11-08
sorry my english is bad.
I add the root password to advance security. When I run the apps (synaptic, etc.) and then system ask me to password, I write the new root pasword, apps not runing again.

---

### Post by earobinson on 2005-11-08
your english was fine, the question was vague when you said "Now not working any apps which requiring root privilege" this could have ment a crash, or that they just dident run (which is the case for you).

ok what you changed was the root password. eg in the log on screen if you type root as your user name and then the password you set you will log on as root (this is not recomended)

also in the terminal you can now type su then the password you set then run apps from the comand line.

however if you type sudo or click on the synaptic icon (that uses gksudo) then you must use the password that you used to log on as the current user.

This is because your current user (assuming its the default user from the install) has root privileges and can run root programs if you type your password.

hope this helps. let me know how it goes.

---

### Post by bobes on 2005-11-08
Thanks, I check this point and write here result tomorow mornig. Nice evening.

---

### Post by bobes on 2005-11-09
Thanks, my problem is solved, all apps working fine.

Nice day.

---

