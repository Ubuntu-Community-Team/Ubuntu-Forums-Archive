---
title: "Error with multiple profiles in Firefox 1.5 ???"
date: 2006-02-24
forum: Desktop Environments
---

### Post by batholith on 2006-02-24
I recently upgraded to Firefox 1.5 using Automatix...however I'm trying to setup multiple profiles for customizing bookmarks etc..(for my wife and I).  I used the command to create two new profiles for my wife and myself:

$ firefox -profilemanager

However when I go to startup the browser, the profile manager screen pops up, and if I select anything other than "default"  I get the following error:

[COLOR="Red"]Firefox cannot use the profile "XXX" because it is in use.

To continue, close the running instance of Firefox or choose a different profile.[/COLOR]

I'm positive that no other Firefox apps are open...I've tried rebooting and still get the same error.  

Anyone out there have a fix?

---

### Post by aysiu on 2006-02-25
First of all, I have to say I've never had luck running separate profiles within one user in Firefox... in Windows or Linux. Your best bet, if you want your wife and you to have separate profiles, is to create separate users in Ubuntu.

[QUOTE=batholith]
I'm positive that no other Firefox apps are open...[/quote] Have you run the command ```
killall firefox
```? > I've tried rebooting and still get the same error. That won't make a difference unless you've gone to System > Preferences > Sessions and marked to not save sessions on logout.

---

### Post by batholith on 2006-02-25
Yep, no firefox apps are running in the background...and the sessions are not being saved....

I'm really wanting to avoid having separate users.

One thing I have noticed, which might help someone diagnois the problem is that if I run the profile manager from terminal:

$firefox -profilemanager

I can rum the separate profiles, no problem.  However if I click on the Firefox shortcuts and the profile manager opens, I get the error message described previously.

I'm a newbie, and I'm not quite sure what the difference is between running the profile manager from terminal versus the shortcut on the desktop???

---

### Post by aysiu on 2006-02-25
Theoretically, there should be no difference.
You're sure your launcher's running the exact same command?

---

### Post by batholith on 2006-02-25
It's probably not exact...the launcher, which gives me the error, is the Firefox shortcut.  The under properties the command for the launcher is:

$firefox %u

I'm not sure how Firefox does it's startup (and all the file and command relationships), but it opens the profile manager first.

So do you think I could just change my launcher command to load up the profile mananger?  Therefore it would read:

$firefox -profilemanager

I'll give it a try...and post the result

---

### Post by batholith on 2006-02-25
Nope doesn't work...I get the same error:

[COLOR="Red"]Firefox cannot use the profile "XXX" because it is in use.

To continue, close the running instance of Firefox or choose a different profile.[/COLOR]


In the terminal I run the command as root and it works...   Can you setup a launcher to run as root and not ask for a password everytime (and only give you root "power" for that command only?).

---

### Post by batholith on 2006-02-25
I've messed around a bit more and have come to the conclusion that if I run Firefox or the profile manager as root I can have multiple profiles, no problems, no errors.

Is there any way to run an app or command from root without asking for a password everytime?

---

### Post by aysiu on 2006-02-25
[QUOTE=batholith]
In the terminal I run the command as root and it works...   Can you setup a launcher to run as root and not ask for a password everytime (and only give you root "power" for that command only?).[/QUOTE] Running Firefox as root is probably not a good idea. Just my two cents. That said, yes, you can make an application launcher run in the terminal. Just check the box that says "run in terminal."

---

