---
title: "Login script for Ubuntu"
date: 2014-02-05
forum: Desktop Environments
---

### Post by Jaxilian on 2014-02-05
Hi
I am trying to get a login script to work in my Ubuntu 12.04 machine and the script is a bash script that uses the variable $USER.

Problem is I can't find a spot to put it so all users that login can run it when they login.

On Gnome is was easy with **/etc/gdm/PostLogin** but Lightdm doesn't seem have that functionality. I tried with lightdm.conf and added the line **session-setup-script = /usr/local/scripts/Loginscript.sh** but it does only so I cannot login graphically at all. The script is executable.

Anyone know how to do this? I seen many posts, but most is about a single user using the machine and not many.

---

### Post by dargaud2 on 2014-02-05
For any kind of login, you can put your script in /etc/profile.d/, but if you are only looking to run something for a graphical login (Gnome/Unity/KDE), I don't know as it likely depends on the window manager. Or maybe, like you said, something in LightDM.

---

### Post by Jaxilian on 2014-03-19
Thanks it worked very well

---

### Post by ian-weisser on 2014-03-19
If you want all users to run it as a user-level Upstart job, you put the trigger in /usr/share/upstart/sessions/

---

