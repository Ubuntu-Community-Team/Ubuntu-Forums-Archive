---
title: "environment variable PAHT does not work in Xwindow"
date: 2005-10-06
forum: Desktop Environments
---

### Post by steveneo on 2005-10-06
I set java/bin to PATH variable in /etc/profile file. It works if I use shell. But when I try to start up Eclipse, it always tell me "it can not find java from PATH variable".  It seems Xwindow skips the /etc/profile. 

So, where can set PATH variable(or others varaibles) for xWindows?

---

### Post by lithorus on 2005-10-06
It's do much Xwindows which skips /etc/profile but rather gdm that starts you session. Can't remember excactly where it reads it's enviroment variables. Will check..

Edit:
It should read the ~/.profile file upon login. You might also try ~/.gnomerc

---

### Post by steveneo on 2005-10-07
./gnomerc works. Thanks.

I am a newbie in Linux, could I ask why linux provides so many configuration files, such as, ~/.profile, .bash_profile, .bashrc etc.  Why don't make things simpler?

---

