---
title: "cant login after restarting X"
date: 2007-02-16
forum: Desktop Environments
---

### Post by NiksaVel on 2007-02-16
Hey all,

I am using gnome on ubuntu 6.10 and one of the problems that are bugging me is that after I restart X using ctrl+alt+bkspc I get the login window, but after I enter my login and password I just get a blank background and the login sound....   not even the splash image...  it just hangs like that...   I can restart it again but no change.   I need to do a full reboot in order to be able to use the system again...


anyone?

---

### Post by hunterP on 2007-02-16
Hey, I am having this exact problem, and the probabilty of it just starting to happen today, for both of us...small.

I think it has something to do with a package upgrade.  I upgraded 2 packages (libmagick9 and one other), then suddenly I restarted X and it hung up in the EXACT way the previous post mentioned.  I rolled back the libmagick9 package but it didn't fix the issue.  If somebody can tell me how to get a history of what the update-manger installed on the system, I can try to downgrade the other package I installed.  

or if you remember what you installed today, let me know


(p.s. so you don't have to go looking: to downgrade a package, in synaptic, select the currently installed package, the in the toolbar: package-> force version and choose the second most recent version).

---

### Post by hunterP on 2007-02-16
Well, I found the solution, it doesn't make sense, but it works.  Don't worry about what I said about the packages, that is wrong.  

For some reason, something called the bonobo-activation-server freezes up, and causes you be unable to login.  If you ctrl+alt+bkspc the GUI and try to log in again, and it freezes on you, simply execute this

```

$ killall bonobo-activation-server

```

Then when you switch back to the GUI (ctrl+alt+f7) you'll see your desktop loading.  For the rest of the time the computer remains on, you should be able to ctrl+alt+bcksp all you like.  

Again, I have no idea why this works, only that it does for me.  Let me know your luck with it.

---

### Post by ophion on 2007-02-16
I doubt that voice login support is enabled.

---

