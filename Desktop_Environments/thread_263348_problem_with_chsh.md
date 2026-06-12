---
title: "problem with chsh"
date: 2006-09-23
forum: Desktop Environments
---

### Post by pranith on 2006-09-23
hi,
    I recently wanted to try out zsh so I changed to it using the command
chsh -s zsh <username>. It worked then, after a few days I want to switch back but now when I try to use chsh -s bash <username>
It gives the following error

chinna-laptop% sudo chsh -s  /bin/bash chinna
Password:
chsh: PAM authentication failed

please help me out with this problem :(
thanks in anticipation 
pranith

---

### Post by sktx on 2006-10-01
You shouldn't need to use sudo to change your own shell.  it should look something like this: 

```
% **which bash**
/bin/bash
% **chsh**
Password: ***<user password goes here>***
Changing the login shell for sktx
Enter the new value, or press ENTER for the default
        Login Shell [/usr/bin/zsh]: **/bin/bash**
% **exit**
```chsh doesn't require you to feed it any parameters, if you just invoke the command, it'll ask you what you'd like to do.  you can set anything as your shell as long as it's listed in **/etc/shells** ... 

if you want to take a look at it, you can do: ```
cat /etc/shells
``` ...from a shell prompt and it'll spit the contents of the file out to your console for you.  

And, if you're ever stuck with a command, you can use the **man** command to view the manual page for whatever command is giving you trouble... for instance, for chsh it would be: ```
man chsh
```Sometimes the man pages are a little sparse or a bit too technical from a beginner standpoint, but they're a good  place to start if you've got a question, so you don't have to wait for someone to respond on the forums.

..*sktx.*

---

