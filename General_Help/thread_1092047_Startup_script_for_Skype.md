---
title: "Startup script for Skype"
date: 2009-03-10
forum: General Help
---

### Post by Yumi on 2009-03-10
Under Preferences - Startup Applications I can automatically start Skype after login.

However, I would like to start two instances of Skype with different Skype Name and Passwords. Additionally I would like the Skype windows to open in workspace 5.

I guess I need two startup scripts which I put into /etc/init.d . How can I include Skype Name and Password as well as Workspace number in the script?

Michael

---

### Post by phinullfermata on 2009-03-10
You can use
```
echo "username password" | skype --pipelogin
```
as the command to login with a certain user (taken directly from skype's man page).

If you have compiz, I would suggest using window rules with the compiz-config manager to set the skype windows to workspace 5.  If not, try installing a package called devilspie.  You can create rules to put the window to a certain workspace.  If you're using this with compiz, the set_viewport command will be what you want, otherwise the set_workspace will be what you need.

Hope that helps.

---

### Post by Yumi on 2009-03-11
Thanks phinullfermata! 

See next reply!

---

### Post by Yumi on 2009-03-12
Success. Now 2 Skype windows open after login and two different skype users (my private and my business account) are logged in.

I wrote two text files and saved them as Skype1.sh and Skype2.sh in /home/myname. Both files I set the permissions to allow "execute as program".

The file contain only
```
#!/bin/bash

echo Skypeuser1 Password1 | skype --pipelogin
```

Then, in "System - Preferences - Startup Applications" I added the two entries: 
Skype1 with the command "/home/myname/Skype1.sh and 
Skype2 with the command "/home/myname/Skype2.sh

Working, but everything opens in Workspace 1

Michael

---

### Post by Gavin Coles on 2010-12-01
I know this thread hasn't been active in a while but I just wanted to say thanks the information provided is excellent.  Now I have all three of my Skype accounts running at log in.

---

### Post by vankich on 2012-02-28
Isn't there a more secure way to login the two accounts than writing your account and password in plain text in a file?

PS: Sorry for bumping an old thread, just it is the right one for my question.

---

### Post by mörgæs on 2012-02-28
Vankich, are you confirming that the information is still valid?

---

### Post by vankich on 2012-02-28
> **mörgæs said:**
> Vankich, are you confirming that the information is still valid?
Yes, it does work.

---

### Post by vankich on 2012-03-01
Is there someone who has idea how to secure the login information at least a little bit (not plain text)?

---

### Post by mörgæs on 2012-03-01
It is better to ask here:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by vankich on 2012-03-02
Thanks for the advice. 

The new thread is [here]("http://ubuntuforums.org/showthread.php?p=11732565#post11732565").

---

