---
title: "HOWTO: hide the directory from the prompt in terminal"
date: 2006-09-21
forum: Desktop Environments
---

### Post by DrZeus on 2006-09-21
[B][COLOR="Navy"][FONT="Fixedsys"][SIZE="2"]how to eliminate the directory from the prompt in terminal:

- open .bashrc from your $HOME directory --ex. pico .bashrc

- locate a line that has something like this:
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '  

//COULD be the second PS1 line you see

- erase the ' :\w\ ' of it

- save the file.  Close the terminal and start a new one; then check by entering to any directory(except the home directory of course)[/SIZE][/FONT][/COLOR][/B]

---

### Post by DrZeus on 2007-02-27
J[COLOR="Sienna"]UST IN CASE YOU SCREW UP YOUR .bashrc FILE:

make this copy:
/etc/skel/.bashrc to your $HOME directory.  It has all the standard setup.
[/COLOR]
[COLOR="DarkSlateBlue"]*thanks to timfrost  and shatrat of the #ubuntu channel for that one*[/COLOR]

---

