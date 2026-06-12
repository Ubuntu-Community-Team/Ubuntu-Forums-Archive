---
title: "problem after update system up to date"
date: 2012-07-27
forum: Desktop Environments
---

### Post by mohdforever on 2012-07-27
hello guys ....

i have an issue with my main admin account in ubuntu 12.04 
last 2 days ago i have updated my system up to date after that it requested to restart my PC .... 

___________

 i tried to log in with my account but it log me out _immediately_ even no background was appeared  .

* just black screen and some commands *

_____________

fortunately, the guest account works well and no problems to log in and to use it.

i  created a new user by terminal  and gave it admin authority .
i  logged in to the new account with no problem.
i was amazed !!!

____

i wonder why this happen only with the main account.
_____________
could you please help me to solve it ??
does someone know how to reset the setting in the main account??


thank you all in advance

---

### Post by bogan on 2012-07-27
Hi!,** mohdforever**,

From the log-in screen, Press 'Crtl+Alt+F1' [0r F2-F6] to get a tty Login prompt [Text Terminal].
Login & enter password [ it will not show] +'Enter'.

Alternatively, (if above does not allow you to login) Boot to recovery, run 'fsck' to reset to Read/Write, and select 'drop to shell'. 
You should not need to login. Enter:```
 ls -Shla | grep -i authority
``` This should give you output like:```
-rw-------  1 user user 53K Jul 27 16:47 .ICEauthority
-rw-------  1 user user  57 Jul 27 16:47 .Xauthority
```Where 'user' is your username: but probably one or the other will be 'root root' instead; and that is the cause of your not being able to login.

Rename the offending file and reboot with: 'sudo mv .filename .filename-old', eg.: ```
sudo mv .Xauthority .Xauthority-old
sudo shutdown -r now
```You should then be able to re-boot & login to your normal username account.

I had exactly this happen after a recent update, and this procedure fixed it OK.

Chao!,** bogan**.

---

### Post by mohdforever on 2012-07-27
thank you so match to reply

i just tried to do these commands but no new effect

thanks so match again

---

### Post by bogan on 2012-07-28
Hi!, 

What output did you get from:
 > ls -Shla | grep -i authoritybogan.

---

### Post by mohdforever on 2012-07-29
-rw-------  1 wonderlife wonderlife 3.1K Jul 29 17:45 .ICEauthority
-rw-------  1 wonderlife wonderlife   58 Jul 29 17:45 .Xauthority


this is the output

---

### Post by bogan on 2012-07-29
Hi!, **mohdforever**,

Thanks for the Post; clearly your no login problem cause was something else.

Probably some problem with compiz settings as it is only your account that is affected.

To reset Compiz.[ after Post by** Frogs Hair**.]
Use Ctrl + Alt + F1 [ or other means ] to enter TTY 
 Login, Enter user name and password  [it will not show ] Press 'Enter'.
Run the following commands per Ask Ubuntu. ```
sudo gconftool --recursive-unset /apps/compiz-1 # Wait until  complete.
sudo gconftool --recursive-unset /apps/compizconfig-1  # Wait until  complete.
```Switch to GUI desktop  (Ctrl + Alt + F7), If needed, first run 'sudo service lightdm start'.

If nothing has changed restart and log into Ubuntu. If that fails repeat  the steps and use the following single command instead of the Compiz reset commands.  ```
 unity --reset 
```Another thing you could try, if resetting compiz does not cure it, is to edit the grub menu script Linux line, with: " ro nomodeset --verbose text", instead of: "ro quiet splash" and see what messages you get. if necessary press 'Crtl+Alt+F1' after attempting a login, to check what new messages come up.

[To edit the grub script, highlight the Ubuntu entry in the grub menu & Press 'e'; the script will show; use arrow keys to scroll cursor to the line that starts "Linux", and along to "ro"; edit and press 'Crtl+x' to boot. The change is not permanent & will have to be repeated if needed.]

It should boot to a tty login prompt, after login & password, enter```
 sudo service lightdm start
```Which in turn should pass you to a normal GUI Login screen; if not press Crtl_Alt+F7 to get to a GUI.

If that does not work either, and does not give you any useful clues try the same but entering "startx" instead of the above; if that works it means the problem is with lightdm or the greeter..

Failing those, the next step I would suggest is to checkout the log files, especially with:```
gksu nautilus /var/log/lightdm
```and its sub-folders.

Best of luck.Chao!, **bogan.**

---

### Post by mohdforever on 2012-07-29
I just tried to do these steps but I got nothing .

anyway, I appreciate that from you and enormous thank for you bro.

^_^

---

