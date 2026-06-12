---
title: "&quot;Get root Access&quot; temporarily to change default Open with app?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by ke3pup on 2006-09-04
hi

I'm trying to change the default Open with application for a few media types, but i can only do it in the Root account but not in the Master account. In the master account i can't change the check box to a different application, i remember in Fedora there was a something called "Get Root Access" in Administrative menu which would give you temporary root privileges for a short period, how can i do that in ubuntu so i can change my Default Open With application? please help.

thanx

---

### Post by reacocard on 2006-09-04
```
gksudo nautilus
```

---

### Post by ke3pup on 2006-09-05
> **reacocard said:**
> ```
gksudo nautilus
```

thanx, but typing that in, has the same effect as if i was to sign in using root account, if i change the Open With in the root account, the Master Account's Default Application hasn't changed. please help.

---

### Post by Titus A Duxass on 2006-09-05
sudo passwd root, then enter your new root password.
To remove the root password - passwd root -d. 
Take a look on the wiki for more accurate info.

---

### Post by ke3pup on 2006-09-05
> **Titus A Duxass said:**
> sudo passwd root, then enter your new root password.
To remove the root password - passwd root -d.
Take a look on the wiki for more accurate info. 
thanx again but why change my password? what's that got to do with anything? i went ahead and did it and now what? i want to change the Default Open With application in the Master Account, not root, but it seems it doesn't allow me to change it from master account as it doesn't have the privileges to do so. Changing it from Root account is NO use as it remains the same in Master Account.

---

### Post by Titus A Duxass on 2006-09-05
Sorry I am not quite following you.

You should now be able to login in as root by typing su and then the password you have just set.  

To leave root type exit.

That should allow you to do anything you want.

---

### Post by Marantz on 2006-09-05
> **Titus A Duxass said:**
> Sorry I am not quite following you.

You should now be able to login in as root by typing su and then the password you have just set.  

To leave root type exit.

That should allow you to do anything you want.

I believe he is talking about being a normal user, in the xdesktop, with root access.

In Fedora there was a little shield thing that would be in the taskbar, that allowed your user, non root user, to perform root tasks without the use of su blah blah, it would go away after awhile.

---

### Post by Titus A Duxass on 2006-09-05
Okay, that explains something.

However I have no experience with Fedora so cannot help him.

I thought he was on the CLI.

---

### Post by toasterofirony on 2006-09-05
Winners use sudo, friend.

It's altogether better way.

---

### Post by Titus A Duxass on 2006-09-05
"Winners use sudo" - This is true.  But every now and again you need to enable root for a specific task.

As long as you disable it as soon as you are finished the risk is minimal.

I used SuSE for a lot of years and that has root enabled, I never had a problem despite having a very, very weak root password.

I often feel that there is way too much paranoia about this subject.  If it is so dangerous or risky why do other distros (including debian) have it enabled?

Remeber this is my only opinion which I am entitled to voice.

---

### Post by toasterofirony on 2006-09-05
Honestly, I'm not sure I've met a task that sudo doesn't do as well as going all root on the system's ***.

Can you give me an example? I'm curious :)

---

### Post by aysiu on 2006-09-05
> **Titus A Duxass said:**
> "Winners use sudo" - This is true.  But every now and again you need to enable root for a specific task. I can't think of a single one, actually... unless you've removed your only *sudo* account from the *admin* group, in which case a root account (also known as "recovery mode") is handy for adding you back in again.

The problem really seems to be that ke3pup has somehow managed to remove permissions or ownership of a configuration file allowing her or him to change the default Open With application.

To ke3pup, try this: ```
sudo chown -R ke3pup:ke3pup /home/ke3pup
``` Substitute in your *actual* username, of course, on all three counts.

---

### Post by ke3pup on 2006-09-05
> **aysiu said:**
> 
To ke3pup, try this: ```
sudo chown -R ke3pup:ke3pup /home/ke3pup
``` Substitute in your *actual* username, of course, on all three counts.

thank you so very much :) now i can change it after enterign your command :).

---

