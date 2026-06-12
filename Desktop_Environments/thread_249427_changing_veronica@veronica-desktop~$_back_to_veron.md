---
title: "changing veronica@veronica-desktop:~$ back to veronica@ubuntu:~$"
date: 2006-09-02
forum: Desktop Environments
---

### Post by fakie_flip on 2006-09-02
How can I change my prompt back to veronica@ubuntu$. I changed veronica-desktop to ubuntu in /etc/hosts and still don't have my prompt back the way it was in Breezy. Thanks.

---

### Post by jimbob on 2006-09-02
The following is from an earlier post of mine.  There is probably a better way to do this but I haven't seen any yet: 

 "There is an environment variable named PS1 that sets this up.

In your home account make a backup copy of the file .bashrc in case something goes wrong.

In .bashrc look for the first line that looks like this:

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

If you edit that line to look like this:

PS1='${debian_chroot:+($debian_chroot)}\$ '

then all you will have for a prompt is the $ sign. You can experiment with the \u@, \h: and \w as you wish to get what you want. Make a change and then open a new terminal window and observe the effect.

Have fun."
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

