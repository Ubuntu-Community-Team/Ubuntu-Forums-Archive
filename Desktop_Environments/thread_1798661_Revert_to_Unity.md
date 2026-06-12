---
title: "Revert to Unity"
date: 2011-07-06
forum: Desktop Environments
---

### Post by sandy_ on 2011-07-06
I had logged in once with Ubuntu Classic as the session and since then whenever the GDM greeter comes up it always selects Ubuntu Classic as the default session. I tried editing the .dmrc configuration but it didn't work out. I want Unity back as the default session.

---

### Post by ajgreeny on 2011-07-06
Use the session menu, bottom right, after choosing your user, but before the password entry.

Presumably that is how you chose classic desktop in the first place, so I'm surprised you did not realise that is how to do it.

---

### Post by TBABill on 2011-07-06
+1 the default will be the last session type you used. Simply choose Unity, login and enjoy. When you logoff or restart you should boot back into Unity. This is done at the login screen where you select your user and enter your password. Choose user, go to the bottom of the screen and choose Unity where it probably now says Ubuntu Classic, then click enter. Do not hit enter until you choose your session type!

---

### Post by sandy_ on 2011-07-07
Problem is even if I select Unity at the GDM greeter as you said and then type in my password, the next time I boot, it still keeps selecting Ubuntu Classic as the default session. Everytime I log in I have to select Ubuntu manually as my session.

---

### Post by grahammechanical on 2011-07-07
Another way to fix this (possibly) is to go to System Settings>Login screen. Unlock the dialog box and from the menu Select ... as default session.

See, if that works.

Regards.

---

### Post by sandy_ on 2011-07-08
> **grahammechanical said:**
> Another way to fix this (possibly) is to go to System Settings>Login screen. Unlock the dialog box and from the menu Select ... as default session.

See, if that works.

Regards.

Tried that too... But didn't work out... :confused:

---

### Post by wojox on 2011-07-08
What does your .dmrc file look like?

---

### Post by sandy_ on 2011-07-08
> **wojox said:**
> What does your .dmrc file look like?

Here's what it looks like :
```

[Desktop]
Language=en_IN
Layout=us
Langlist=en_IN:en
LCMess=en_IN.UTF-8
Session=gnome

```

---

### Post by wojox on 2011-07-08
Delete the *Session=gnome* and see what happens.

---

### Post by sandy_ on 2011-07-11
> **wojox said:**
> Delete the *Session=gnome* and see what happens.

That didn't work either. After I rebooted it kept selecting Ubuntu Classic by default. :confused:

---

### Post by Krytarik on 2011-07-11
sandy_, in fact GDM pulls in "/var/cache/gdm/USERNAME/dmrc" upon the first login:
[https://defect.opensolaris.org/bz/show_bug.cgi?id=14575#c5](https://defect.opensolaris.org/bz/show_bug.cgi?id=14575#c5)

So, please check the content of this file, and also -and specifically- its permissions, they should be 644 and owned by your user.

Greetings.

---

### Post by sandy_ on 2011-07-17
> **Krytarik said:**
> sandy_, in fact GDM pulls in "/var/cache/gdm/USERNAME/dmrc" upon the first login:
[https://defect.opensolaris.org/bz/show_bug.cgi?id=14575#c5](https://defect.opensolaris.org/bz/show_bug.cgi?id=14575#c5)

So, please check the content of this file, and also -and specifically- its permissions, they should be 644 and owned by your user.

Greetings.

There was a problem with permissions here. A chmod did the trick. Thanks for the help...

---

