---
title: "How do I restore to a working point?"
date: 2008-12-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kms017 on 2008-12-20
I'm VERY new to Ubuntu and I've been searching for hours but I cant find any answers, please help!

I have a new Dell mini that loads all the way up till it comes to the Ubuntu log in screen thats when I get an error message saying, "Your home directory is listed as: '/home/katie' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you usea failsafe session.". The only failsafe session that will work is a terminal failsafe and while I know how to get in there honestly I dont know what to do once I'm there. As it is brandnew I'm not worried about losing any information but I dont have my external drives to restore using my disks is there a way to restore from the failsafe terminal session? PLEASE HELP!

---

### Post by pytheas22 on 2008-12-20
This is strange, but it shouldn't be too hard to fix.  Please answer these questions:

1. did the system ever work, or did it come with this problem out-of-the-box?  If it used to work, what changes did you make since the last time you successfully logged in?

2. what is the output of this command typed in a fail-safe terminal:

```
ls -l /home/katie
```

(Note that that's a lowercase L, not a 1, above.)

3. run this command, which will create a new user named 'testuser':
```

sudo adduser testuser
```

After setting a password for the new user and answering other questions as prompted, log out of the fail-safe terminal and try logging into the desktop as the user 'testuser'.  Does this work?

---

### Post by kms017 on 2008-12-20
1. Yes it worked however when I foolishly allowed my sister to use it, it returned like this.

2. No such file or directory

3. Tried this and when it prompts for a password it wouldnt allow me to type anything.

---

### Post by pytheas22 on 2008-12-20
> Tried this and when it prompts for a password it wouldnt allow me to type anything.

Sorry, should have warned about this: you don't see anything on the screen when you type in the password, for security reasons.  Just type it and press enter, and it should allow you to create the new user account.  Please try this and then try logging in as the new user; I think that this will solve the problem.

If not, we can create a new /home folder for your user 'katie' (it looks like your whole /home folder got deleted entirely, which is weird, but explains the problem you're having), but just creating a new account entirely would probably be an easier solution.

---

### Post by kms017 on 2008-12-20
Ok, the testuser thing worked but I still got the error message at log on, will this always happen or can we fix this?

Thank you so much for all your help so far!

---

### Post by kms017 on 2008-12-20
I just managed to fix the problem using the testuser name! Thank you so much for all your help!

---

### Post by pytheas22 on 2008-12-20
I'm glad it's fixed.  You probably don't have administrative rights under the testuser account, right?  Is that a problem?  Or did you manage to fix it so that you can log in as 'katie' again too (where you would have administrative privileges)?

Also, in the future, if you want to let people play with your laptop, you can have a user account with non-administrative privileges available for them to use.  This way, they can't mess up your stuff or your system!  The latest version of Ubuntu, 8.10, includes a restricted-access account by default, but I think the Dell Minis come with 8.04, so you wouldn't have this feature.  But you can easily create an account manually.

---

