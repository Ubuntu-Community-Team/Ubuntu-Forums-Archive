---
title: "Ubuntu 14.04 returns to login screen"
date: 2014-05-09
forum: Desktop Environments
---

### Post by Jurjen de Vries on 2014-05-09
I did a fresh install of Ubuntu 14.04 64bit desktop last week. After installing the nvidia driver and tweaking some things by installing Unity Tweak Tool software, my desktop won't let me login anymore.
I got the regular login screen, after giving my password it gives a black screen for a few seconds and then returns to the login screen again. I am able to start a guest login session successfully.

Any clues how to fix this? If not, any clues which log files etc to look at the get more information which causes this problem.

Thanks in advance.

---

### Post by chester-z on 2014-05-09
I've just upgraded from 13.10 to 14.04 and after rebooting at the end of the installation I had the same problem. Ubuntu returns to the login screen after I type the correct password. I can logon as guest.

---

### Post by chester-z on 2014-05-09
I have tried some of the things on this page: [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop) but it didn't solve my problem. So I did a clean re-install and now I don't have any problems.

---

### Post by Jurjen de Vries on 2014-05-10
Thanks for that link chester-z

[COLOR=#333333][FONT=UbuntuRegular]Removing the [/FONT][/COLOR]~/.Xauthority[COLOR=#333333][FONT=UbuntuRegular] file then rebooting solved my issue., from [/FONT][/COLOR]http://askubuntu.com/questions/455327/unable-to-login-to-14-04-after-successful-installation

---

