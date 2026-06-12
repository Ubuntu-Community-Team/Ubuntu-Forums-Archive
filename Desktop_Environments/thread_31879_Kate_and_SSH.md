---
title: "Kate and SSH"
date: 2005-05-05
forum: Desktop Environments
---

### Post by domzo on 2005-05-05
This isn't really Hoary specific but I couldn't work out which forum to post in...

I want to use Kate to edit a file on a remote machine that doesn't have Kate installed

Is there a way to ssh to that machine but use my local installation of Kate to edit the file.

I have tried:

kate ssh me@theremotemachine: /home/users/me/thefile

but that doesn't work.

Please don't make me use VI !

---

### Post by dave9191 on 2005-05-05
When you ssh into another machine, you can only use what they have installed. You can however copy a file using sftp, edit it and copy it back over. And there are some text editors (i only heard that emacs can do this with the right plugin) that will allow you to edit remote files throught ssh. I had a quick look for such a plugin for kate, but didnt find one. Also if you cant stand vi, try nano :)

---

### Post by domzo on 2005-05-05
Many thanks Dave, I thought that might be the case.. 

I can copy the file over, but I will want to save it & recompile several times so it will be a lot of back and forth.

The remote machine doesn't have nano - so I guess it's emacs or VI ...  :mad:

---

### Post by mikl on 2005-05-05
[QUOTE=domzo]This isn't really Hoary specific but I couldn't work out which forum to post in...

I want to use Kate to edit a file on a remote machine that doesn't have Kate installed

Is there a way to ssh to that machine but use my local installation of Kate to edit the file.

I have tried:

kate ssh me@theremotemachine: /home/users/me/thefile

but that doesn't work.

Please don't make me use VI ![/QUOTE]

What about using the fish kioslave - use the open-dialog of Kate, and just type fish://adress-of-other-machine and type enter - then you'll be prompted for your username and password for the remote machine.

The fish kioslave makes it possible to browse and handle files on remote machines like you browse normal files, by utilising the ssh-protocol and simple unix-commandline program, ls, cat etc.

This also have the benefit that all communication between yourself and the remote server is encrypted  \\:D/

---

### Post by domzo on 2005-05-05
You beauty!

That works perfectly - thanks.  :)   Now I can stop having to scp and type my password every 5 minutes.

---

### Post by dave9191 on 2005-05-05
mikl that is soo cool :D

I completly forgot about fish and didnt even think about trying to put sftp as a file location. KDE just keeps getting better and better :D

Nice one. 

And sry for misleading you a little domzo.

Dave

---

### Post by domzo on 2005-05-05
No probs. We've both learnt something!

---

