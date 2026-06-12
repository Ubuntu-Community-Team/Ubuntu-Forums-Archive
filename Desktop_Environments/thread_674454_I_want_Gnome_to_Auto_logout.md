---
title: "I want Gnome to Auto logout"
date: 2008-01-21
forum: Desktop Environments
---

### Post by bbabiuk on 2008-01-21
I have seen posts asking how to disable Gnome from auto logging out.  My question is a little different.  I have Ubuntu 7.10 installed.  I finally got my wife up and running using Ubuntu, but she never logs out of her account.  (Its just easier to find a way to get it to log out for her as I have tried stepping her through the process - despite my efforts it continues).  Anyhow, she typically leaves the computer logged into her account, so when I come to the PC it is there on her screen.  Is there a way to make Gnome auto logut her account after so long of inactivity?

Thanks.

PS> Sorry if this was posted elsewhere, I searched couldn't find anything.

---

### Post by diaa on 2008-01-23
**Sorry, misunderstood your question, please ignore this reply**

From the main menu, just go to *System > Preferences > Screensaver* and uncheck *Lock screen when screensaver is active*, your computer will stay working for as long as you want without activity, without requiring to type in your password

---

### Post by bbabiuk on 2008-01-23
But that isn't really asked.  I wanted Gnome to auto logoff my wife's account if possible.  Not leave it up, not lock the screen.  I want the account to log off, thus forcing her to logon each time she comes to the pc.  (not to mention, I can run my account without having to log her off first)

---

### Post by diaa on 2008-01-23
> **bbabiuk said:**
> But that isn't really asked.  I wanted Gnome to auto logoff my wife's account if possible.  Not leave it up, not lock the screen.  I want the account to log off, thus forcing her to logon each time she comes to the pc.  (not to mention, I can run my account without having to log her off first)

Sorry about my previous post, I did some searching and I think I can give you some hints.
first, the command that allows you to logout is
```
gnome-session-save --kill --silent
```It's possible to have a logout button on the lock dialog by changing some settings, I think this is not exactly what you want but it's very close, you'll be one click away from logging out when your PC is left idle.
Here's how to add a Logout out button to the lock dialog:[LIST=1]
[*]Press Alt+F2 then enter
```
gconf-editor
```This is a program that configures gnome internals(somehow like Windows registry editor).
[*]Open *Apps* folder in the left pane then select *gnome-screensaver* folder, now you'll see gnome-screensaver settings(known as keys) in the right pane.
[*]Check *logout_enabled* key
[*]Change *logout_delay* key to 0(double-click on it, then put 0 in *Value* field).
[*]Change *logout_command* to the logout command I mentioned above[/LIST]Now, when you lock your PC manually or when it locks out automatically due to inactivity, you should see the Log Out button in the dialog.

---

### Post by fancyl on 2008-02-29
I am in a similar situation, but with my coworker and our shared computer. He never logs out. Not only is it risky, security-wise, but it's also annoying that I have to constantly log out for him so I can log in.

Any help would be really appreciated.

---

