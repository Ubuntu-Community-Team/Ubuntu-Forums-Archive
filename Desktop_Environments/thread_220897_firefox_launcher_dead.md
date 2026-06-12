---
title: "firefox launcher dead"
date: 2006-07-22
forum: Desktop Environments
---

### Post by ndyguy on 2006-07-22
My firefox launcher in my toolbar is no longer working (I'm sure I did it, but don't know how to fix it).  When I click on it it says "Could not lauch application    Details: Failed to execute child process "firefox" (No such file or directory)"

The command in the launcher properties is "firefox %u"  And when I go to /usr/lib/firefox and open the shell script firefox still works just fine.

Can anyone point me in the right direction?

---

### Post by Ziox on 2006-07-22
have you tried to create another launcher by going to the main menu, find firefox, then right click and add to panel...

perhaps that would "solve" it

---

### Post by SimonJW on 2006-07-22
Can you run firefox by typing "/usr/bin/firefox" into a Terminal?

If not, you are missing a file, which can be created by:
```
sudo ln -si /usr/lib/firefox/firefox /usr/bin/firefox
```
I'm not sure how this file could have gone missing, but the only way I can see of the Launcher not finding it is if
a) This file is missing, or
b) /usr/bin is not in you Path

but if it where b) a lot of other applications would almost certainly be having problems too, so I think it is a).

Let us know if that works!

---

### Post by ndyguy on 2006-07-22
> **SimonJW said:**
> Can you run firefox by typing "/usr/bin/firefox" into a Terminal?

If not, you are missing a file, which can be created by:
```
sudo ln -si /usr/lib/firefox/firefox /usr/bin/firefox
```

. . .

Let us know if that works!

Thanks, that fixed the problem.

---

