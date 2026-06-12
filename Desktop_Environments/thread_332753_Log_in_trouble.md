---
title: "Log in trouble"
date: 2007-01-06
forum: Desktop Environments
---

### Post by ronbrooks on 2007-01-06
Hope someone can help me on this one.

I have two accounts on this computer.  Account one works fine.  Account two will not log in and when we do try we get an error message.

Can not start the session due to some internal error.   From that window they give you a view details (~/.xsession-errors) In there I found this

session_child_run; could not exec /etc/gdm/Xsession default.

I have only been on Linux for about a month and need help with the problem so that my second account will be able to long in also.

---

### Post by Stemp on 2007-01-06
Do you have the same problem if you create a new user ? (a third one)

---

### Post by ronbrooks on 2007-01-06
Yes I get the same think.  I tryed to delete the account and reenter it but no change.  I used a new account and password but still got the same thing

---

### Post by kidders on 2007-01-06
Hi there,

Do your new users have access to all the appropriate stuff (for instance, your video devices)? You should take a look at your own secondary group memberships, and see which ones you think might be important for other local users to have. This *might* be the cause of your trouble.

How much access users have to your system is a matter of personal choice, but Linux will tend to be as mean as possible, unless instructed otherwise, for security reasons.

---

### Post by ronbrooks on 2007-01-06
That user has everything except Adm access.  That account was working just fine up to a couple weeks ago and there have been some updates to the system from the update manager. Is there a command in terminal that will re configer that account. or at least look at it and see it there is something wrong with it.  To me it looks like something went hay wire with it.

---

### Post by Stemp on 2007-01-06
```
stemp@caderousse:/var/log$ ls /etc/gdm/Xsession -l
-rwxr-xr-x 1 root root 6534 2006-09-21 11:07 /etc/gdm/Xsession
```

Same permissions ?

---

### Post by ronbrooks on 2007-01-06
Well I get the same as you do on that command. 

 I hope I don't have to reinstall again.  It takes so long on dial up to set up everything again.  The updates took me all night to down load them. Then I will have to down load the prgrams and set them all up again.  

So if you can help please do.

---

### Post by Stemp on 2007-01-07
Can you connect in terminal mode with this user ?

---

### Post by ronbrooks on 2007-01-07
OK I don't know what I did but I loged into that account under a new session Failsafe GNOME and it let me in.  I changed some of the setting and loged out.  Then I did a reboot and tryed to log into that account again and it let me in. So I guess it was a setting that was off.  It may have been a screen saver or a background picture that was holding it up.

Thanks for your help.

---

