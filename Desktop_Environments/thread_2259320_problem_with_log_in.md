---
title: "problem with log in"
date: 2015-01-03
forum: Desktop Environments
---

### Post by blackvm on 2015-01-03
I can't log in into my session because after i insert the password i got blank screen and i can't log to the desktop, but if i choose guest session at login screen the desktop start normally, I don't know what is the problem so can anyone help me and sorry for my english.

---

### Post by whitesmith on 2015-01-03
Can you login from a tty? To help us diagnose the problem, do a Ctrl+Alt+F1, login there, and do a Ctrl-Alt-F7 to go back tol the black screen. Try this and post the results.

---

### Post by blackvm on 2015-01-03
I can login from a tty with Ctrl+Alt+F1 but that's happen if only I press Ctrl+Alt+F1 before typing the user password in the login screen (I mean before I choose the session )
but if I login and the black screen comes I can't use tty (if I do Ctrl+Alt+F1 or Ctrl-Alt-F7  nothing is happen )

---

### Post by whitesmith on 2015-01-03
This is totally unexpected. You should always be able to go back to the GUI session with Ctrl+Alt+F7 after you've logged in. The fact that Guest works tells me that Ubuntu  is mostly OK, but there's a serious problem with your account. Since this installation is brand new (I'm assuming that) why not wipe it with another installation and try again? You have no investment except time so it seems the best approach. Later.

---

### Post by Jack Waugh on 2015-03-12
This has been happening to me in Xubuntu.  I had "set -u" in my .bashrc.  When I removed the "set -u" command, the problem went away.  But in my case, I was always able to use a tty console.

---

