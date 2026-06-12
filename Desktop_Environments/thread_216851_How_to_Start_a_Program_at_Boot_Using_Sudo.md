---
title: "How to Start a Program at Boot Using Sudo"
date: 2006-07-16
forum: Desktop Environments
---

### Post by larry on 2006-07-16
Hello,

I recently learned how to export a directory to my path by editing the bash_profile file.
Now, I also need to start automatically, every time I switch on the machine, a service as a superuser.
Of course I want everything to take place "silently" without being prompted for a password.
Which file should I modify for that? And how?
Many thanks

Larry

---

### Post by Ramses de Norre on 2006-07-16
```
export EDITOR=gedit
sudo visudo
```
Add a line like this: ```
ramses ALL= NOPASSWD: /usr/sbin/firestarter
```
this line would enable user "ramses" to start "/usr/sbin/firestarter" without a password.
You might need to run ```
xhost +
``` in order to get it working.
Then you go to system > preferences > sessions and add "sudo command" or "gksudo command" in the startup tab list with an order of 50.

---

