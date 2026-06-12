---
title: "su segmentation fault error in terminal"
date: 2009-02-19
forum: General Help
---

### Post by alexandrupop on 2009-02-19
Hi,
Since a week or two my Ubuntu installation (with KDE 4.2 on top) cannot update itself using the GUI updater( I tried with Adept and the Gnome updater as well). Also I noticed that I cannot change the session to Gnome anymore( my default session is now KDE instead of Gnome).
Every time I try to run any update the updater window just disappears after I enter my root password. If I try to run an update in the command line I have a "Segmentation fault" error no matter what combination of commands I put in ( all starting with su of course).
I was a bit puzzled about the source of the issue until i found out that even if I run only the su command in the terminal it errors out with a "Segmentation fault" immediately after i enter my password and hit enter.
Please help - i don't want to reinstall Ubuntu

---

### Post by alexandrupop on 2009-03-19
Still no joy.
However if I try to do strace for su to a file the error message that appears after I type my password is "authentication failure" instead of "segmentation fault". When I try su again without prepending strace I have the same segmentation fault error as before.
I attached the strace output for the su command maybe someone has any clues.
Cheers

---

