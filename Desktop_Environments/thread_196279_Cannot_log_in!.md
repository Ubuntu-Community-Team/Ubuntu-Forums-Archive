---
title: "Cannot log in!"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Z13 on 2006-06-14
When I try logging in from the startup screen using the system default session, a window appears telling me that my last session must be lasted less than 10 seconds or that I have installation problems ("if you haven't logged out yet"). This is the first time when smth like this happens to me in 2 weeks since I've started using Ubuntu Dapper.

Naturally I wanted to see the error report presented on the same one-button (OK) window. It sounds smth like this: "usr/share/dbus-1/services: no such file or directory".

I logged in then using a safe Gnome mode and checked for the directory. Stunned: the directory IS there and have all the run-at-startup programs' files.

Please smb tell me what should I do or what is the cause. How do I repair my Ubuntu??

---

### Post by caserio on 2006-06-14
Hi,
 Try this:

 Press CTRL + ALT + F1 and log in. 
 Then type:
 rm -r /home/*your_user*/.ICEauthority

 After that press CTRL + ALT + F7 and log in again.

---

### Post by aysiu on 2006-06-14
How about instead of deleting the .ICEauthority file, you just set it to the proper permissions? ```
sudo chown z13:z13 ~/.ICEauthority
sudo chmod 600 ~/.ICEauthority
``` Though, if you're not able to log in, you might not be able to log in even after pressing Control-Alt-F1. You may need to boot into recovery mode.

---

### Post by Z13 on 2006-06-14
I don't think I made myself understood: I can't log in as root either. Please read again my first post and tell me what should I do.

It doesn't work the way Aysiu said and can't afford deleting anything 'till I know what I'm actually doing.

---

### Post by aysiu on 2006-06-14
So what happens when you select recovery mode from the Grub menu?

---

### Post by Z13 on 2006-06-14
When I boot Ubuntu under recover mode I believe it's checking lots of stuff, then it appears the welcome/logging screen and nth is changed (meaning I still can't log in as root or super_user(me) using the system's default session).

---

### Post by aysiu on 2006-06-14
What's nth?

Why do you get a welcome/logging screen?

In recovery mode, there should be no screen.

It should be text-only, white on black, with a root prompt.

---

### Post by Z13 on 2006-06-14
Sorry: nth = nothing.
I said that after the recover mode finishes all the checks or whatever it does (and, yes there is no logging screen there, but console), I'm starting again Ubuntu and THEN is appears that welcome/logging screen I was talking about.
And NOTHING is changed: still I cannot log in.

---

