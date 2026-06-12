---
title: "XServer Failure On Boot"
date: 2008-01-05
forum: Desktop Environments
---

### Post by Mojosdad on 2008-01-05
Once again Ubuntu has done its best to completely destroy itself for no apparent reason

Power PC down in usual way, no problem. Power PC up, and it boots into a console login. Tried to 'startX', works, but no power down options on menu, only log off. Know that 'sudo shutdown 0' will normally power down so try it.

But only get into single user mode. Sudo reboot works but once again no graphical login screen and only logoff option on power menu.

Have tried the following:

deleting .Xauthority files from /home
reinstalling kdm
dpkg-reconfigure kdm
dpkg-reconfigure xserver-org

Have checked that the graphical shutdown options are enabled in KControl


I have plenty of room on /home. The only thing thatis different is I have started to get messages about /var/tmp/<somefile> is owned by UID 1000 instead of 0. UID 1000 is my userid. I have not CHOWNed these file.

Does anyone know how to fix this problem? I have already had to compile a kernel myself to enable DMA support and if it means a complete reinstall to fix, it's not likely to happen since Windows is already on the other drive

---

### Post by boban on 2008-01-05
> **Mojosdad said:**
> Tried to 'startX', works, but no power down options on menu, only log off. Know that 'sudo shutdown 0' will normally power down so try it.

When you use startx from terminal, then you won't have shutdown button in a menu. 
> Does anyone know how to fix this problem? I have already had to compile a kernel myself to enable DMA support and if it means a complete reinstall to fix, it's not likely to happen since Windows is already on the other drive

What happens when you type: ```
 sudo /etc/init.d/kdm start 
``` after loging in into console?

---

### Post by Mojosdad on 2008-01-05
> **boban said:**
> 

What happens when you type: ```
 sudo /etc/init.d/kdm start 
``` after loging in into console?

I get a message that KDM is already running

---

### Post by Mojosdad on 2008-01-05
OK maybe some useful testing performed this end.

I normally use auto login (I'm the only user). If I turn this off, the the desktop boots normally. Turn it back on, boot into console. Turn it on, burn with 15s delay insead of none, bot into desktop.

So is there a possibility that recent updates have broken the auto-login feature such that login fails and the user drops into the console?

---

### Post by boban on 2008-01-05
> **Mojosdad said:**
> I get a message that KDM is already running

The try ```
 sudo /etc/init.d/kdm restart 
```. Does it produce any error?

---

### Post by boban on 2008-01-05
> **Mojosdad said:**
> 
So is there a possibility that recent updates have broken the auto-login feature such that login fails and the user drops into the console?

Or mayby you are logged and somehow ubuntu is dropping you to another console? After login into terminal try: ```
who
``` to see who is logged on.

Also try pressing ctrl+ alt + F7 from terminal.

---

### Post by Mojosdad on 2008-01-05
'who' says I am only user logged on tty2

restart kdm logs in.

If I use auto-login at 10s, I get successful boot first time. restart KDM also successful with 10s wait for login, so problem seems to be in having KDM start

---

### Post by boban on 2008-01-05
> **Mojosdad said:**
>  so problem seems to be in having KDM start

Exactly... It seems like you are not the only one with this  problem, e.g. [http://ubuntuforums.org/showthread.php?t=383047](http://ubuntuforums.org/showthread.php?t=383047)

I will search a little bit more... maybe I will find a solution...

---

### Post by boban on 2008-01-05
> **boban said:**
> I will search a little bit more... maybe I will find a solution...

Unfortunately I didn't find anything useful :(. I hope somebody else will help you.

---

