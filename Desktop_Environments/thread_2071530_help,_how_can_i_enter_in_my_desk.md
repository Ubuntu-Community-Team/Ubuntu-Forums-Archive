---
title: "help, how can i enter in my desk"
date: 2012-10-15
forum: Desktop Environments
---

### Post by al kang on 2012-10-15
I just began to use Ubuntu 12.04. single system
today I turned on my laptop,  after I inputed in the password, the screen didn't turn out to be my desk environment, but enter into the login page again!!!!
I tried many times, it is no use. 
then I make a new user account, it is no problem to login using the new account. but the old one still couldn't . 
what is the problem? 
please help me!!!!!!!!!!how can I do?  
thanks in advance

---

### Post by Bashing-om on 2012-10-15
al kang; Hi ! Welcome to the forum.

Can it be that the the sudoer file permissions are changed?
Check:  is ".ICEauthority"  owned by you:
 At the login screen, press Ctrl+Alt+F1 to get to the console.
 Log in there.
enter into terminal:
```
ls -al .ICEauthority 
```If it isn't (but possibly by root), change it to you:
```
sudo chown USERNAME:USERNAME .ICEauthority

``` Switch back to the login screen by pressing Ctrl+Alt+F7 
Try again to log in.
If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[INDENT]hth && Warm regards <==BDQ

[/INDENT]

---

### Post by al kang on 2012-10-16
I have tried, but it is no use.
the computer still stay on the login screen.

---

### Post by al kang on 2012-10-16
It is OK using other user account but the old one.  and for the old account there is a cycle on the login screen. even when I input arbitrarily  wrong passwd, there will be warning,and ask me to try again!!

---

### Post by al kang on 2012-10-16
the pictures show
1. using the user "kang"
2.input the correct passwd
3.push enter button then return to the login screen
4.input a wrong passwd, enter, then there will be the warning(red words)
using the other two user name , there is no problem

---

### Post by spjackson on 2012-10-16
In all probability, something is broken in your desktop settings. In my experience, this can be difficult to diagnose.

The way I would go about this is to rename my home directory, create a new empty home directory (owned by me), login successfully to my desktop, then gradually more across stuff from my renamed directory.

So logged in as you from a console:
```

cd /home
sudo mv $USER $USER.old
sudo mkdir $USER
sudo chown $USER:$USER $USER
ls -l # check that permissions are the same on $USER and $USER.old

```

I'm not saying that this is the best thing to do, just that this is what I would probably do in a similar situation (and have done on very rare occasions).

Alternatively, there may be clues in ~/.xsession-errors that may enable you to identify the fault.

---

### Post by al kang on 2012-10-16
it is done , thx  very much

---

