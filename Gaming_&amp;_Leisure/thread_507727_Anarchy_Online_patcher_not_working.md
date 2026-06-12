---
title: "Anarchy Online patcher not working"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by AmazingJustin on 2007-07-23
When I am updating using the patcher I get an error that says I need to be logged in as administrator or give AO permission to write a local file.  How would I give AO permission to do this?

---

### Post by mafarlou on 2007-11-14
I had a similar problem when installing with wine also. the best solution that i found is:

1) disable your internet connection

2) in terminal type sudo nautilus

3) enter your password, hit enter

4) browse through your system to your AO directory

5) right click it and go to properties, then permissions

6) change the permissions to allow read/write to all of the available (groups, users, other) 

7) keep it like that since AO patches like every other day haha.

*if that doesn't work*

1) log into a tty (ctrl+alt+F2 is my favorite) login as root, type the password

2) type chown (your username) filename

3) after that you should be able to do the first steps that I told you about.

If you need anymore help, log onto AORC and send a tell to either Huglarth(my main) or Tyromert(my alt in progress) and i'll try to help (i'm on RK1)

good luck

---

