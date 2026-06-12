---
title: "[Xubuntu] Getting logged out repeatedly"
date: 2013-08-02
forum: Desktop Environments
---

### Post by Spectro87 on 2013-08-02
I've been having this problem for a few days now. I'm getting repeatedly logged out of Xubuntu. I  have also had a new option come up after logging in that lets me load a  session. I've just been loading default and I'd like to know how I can  get rid of this screen as I don't use it as well as find out why I'm being logged out. I'm  also noticing an error message everytime I get to the desktop that says  "Invalid option: -session".

---

### Post by Toz on 2013-08-02
Which version of Xubuntu are you using? 

>  I have also had a new option come up after logging in that lets me load a session. I've just been loading default and I'd like to know how I can get rid of this screen as I don't use it as well as find out why I'm being logged out.
If 13.04 or later (Xfce 4.10), you will find a "Clear Saved Sessions" button located at Settings Manager -> Session and Startup -> Session tab. This will delete the saved sessions that you are being prompted for. Also, when logging out, you will have the option to Save the current session. If you don't want the sessions saved, then make sure the checkbox is unchecked.

If however, you are on an earlier version of Xubuntu (Xfce <= 4.8), you will have to manually clean out the sessions cache by:
1. log out
2. Go to first tty (Ctrl+Alt+F1)
3. login to the text console
4. Enter the following commands:
```
cd $HOME/.cache
rm -rf session
```
5. Go back to the GUI (Ctrl+Alt+F7)
6. Login

> I've been having this problem for a few days now. I'm getting repeatedly logged out of Xubuntu.
...and
> I'm also noticing an error message everytime I get to the desktop that says "Invalid option: -session". 
...may get resolved by clearing the session cache as noted above. If not, there may be some helpful information in your $HOME/.xsession-errors log file (since your X session is crashing, you'll need to look at the previous log file after you log back in). To have someone else look at it, from a terminal window, run:
```
pastebinit $HOME/.xsession-errors.old
```
...and post back the link that is generated.

---

### Post by pqwoerituytrueiwoq on 2013-08-03
try updating xfce4-session to the version in proposed, i assume you are using xubuntu 13.04

---

