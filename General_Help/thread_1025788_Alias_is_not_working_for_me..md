---
title: "Alias is not working for me."
date: 2008-12-30
forum: General Help
---

### Post by KeilanS on 2008-12-30
Hey everyone,

I am trying to use Alias in my terminal, but everytime I close the terminal the alias commands reset. Here is what I'm been typing in.

First I do "cd ~" to get me into my home directory, then I type
```
alias ll='ls -l'
```

This works fine until I close the the terminal, however, on reopening a terminal the alias command no longer exists, and ll results in it saying it doesn't recognize the command.

Help?

Thanks in advance,
Keilan

---

### Post by Bluebell392 on 2008-12-30
An alias in a terminal window only lasts until you close the windows, as it is only valid for the current bash session. To make it permanent, write a file with the extension .sh in a plain text editor, like gedit, kate or nano, and the file has to contain this: ls -l. Move it to /usr/bin, make executable with sudo chmod a+x /usr/bin/thefile.sh where thefile is the name of the file.

---

### Post by taurus on 2008-12-30
Edit ~/.bashrc

```
gedit ~/.bashrc
```
and add this line to the end of it.

```
alias ll='ls -l'
```
Save it and close down the gedit editing window.  Then, run

```
source ~/.bashrc
ll
```

ll should be good from now one everytime you open a terminal.

---

### Post by jpkotta on 2008-12-30
Add it to your ~/.bashrc.  Whenever a shell starts it's a blank slate.  It looks at several files, including ~/.bashrc, to get settings.

---

