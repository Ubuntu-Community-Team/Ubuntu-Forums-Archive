---
title: "Unable to copy the user's Xauthorization file"
date: 2008-09-20
forum: Desktop Environments
---

### Post by gmbrammer on 2008-09-20
I get this error message, "Unable to copy the user's Xauthorization file",  when I try to execute any of the administrative commands requiring root privileges. When I check my xauthority with the xauth command, I find that my Xauthority file is /tmp/.gdmXXXXX not in my home directory as .Xauthority.  I cannot find where the xauthority file is created at start up time.  I think that my error message is somehow tied to the creation of the xauthority file in /tmp.  I have tried merging the entries in the /tmp/.gdmXXXXX file into my home directory file .Xauthority, but I still get the error.  If I remove the /tmp/.gdmXXXXX file, a new /tmp/.gdmXXXXX file will be created with a new XXXXX.  I have tried searching for the error message and found many things to try, but none worked.

---

### Post by aysiu on 2008-09-20
Can you try booting into recovery mode and then typing ```
chmod 1777 /tmp
chown root:root /tmp
exit
``` ?

If you don't know how to boot into recovery mode, check out the first half of this tutorial: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by gmbrammer on 2008-09-21
Thanks for the chown/chmod idea.  I had already implemented it, but I tried again with no change in the root access permission on administrative tasks via the menus. sudo admintask works OK. I was able at correctly create a .Xauthority file in my home directory but the same problem is still there.  However, I am unable to use xauth as root to create a .Xauthority file.  When I use the generate command in xauth, I get the message "unable to open display: hostname/unix:0".  I tried various version of the display name even tried setting the shell variable "DISPLAY="hostname/unix:0)" - same error message.  Somehow the admin acct cannot become root via the mechanism used in the run as root from the System menu.

Do you have any other ideas?

Thanks.

---

### Post by aysiu on 2008-09-21
My ~/.Xauthority file is owned by *username* and is chmoded to 600

I don't have an Xauthority file at all in /tmp

I do have a /tmp/.XO-lock file, though, owned by root with 222 permissions.

Not sure if that info helps at all.

---

### Post by gmbrammer on 2008-09-22
:popcorn:My ~/.Xauthority is chmod 600 and is owned by me group is me.  When I set XAUTHORITY value to /home/me/.Xauthority, I get the correct items in the file.  However, I still cannot access the administration menu items that ask for my password to run.

Your suggestions were appreciated.

---

