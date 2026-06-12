---
title: "i typed sudo chmod 700/home-can only use failsafe terminal"
date: 2008-06-20
forum: Desktop Environments
---

### Post by Seaniesean on 2008-06-20
Hello, i typed sudo chmod 700 /home into terminal to try and fix some error about "should have 655 permissions or something" at login.  Now i can only use failsafe terminal.  How can i correct this error so i can use ubuntu properly again? Please help!

---

### Post by Seaniesean on 2008-06-20
Actually, someone just answered me in the archived thread, so feel free to delete this.  The answer was "sudo chmod 755 /home" for anyone who gets this problem and ends up here.

---

### Post by Seaniesean on 2008-06-20
well, that failed miserably.  i must have done something else.  I saw some thread and tried some other stuff too, involving chown, chgrp...etc.etc.  if i type in these, i get some security warning now, which is an improvement of sorts over "your login lasted less than 10 seconds"

Any other ideas?  I think i'm going to put a spectrum 48k on one of my partitions, just so that i'll actually have an "operating system" that works all the time.

---

### Post by sisco311 on 2008-06-20
ok. try this
```
sudo chmod 0755 /home
sudo chown -R $USERNAME. $HOME
sudo chmod 0750 $HOME
chmod 0644 $HOME/.dmrc
```don't  change anything in the commands.  Ignore the                               *chown: cannot acess /home/username/.gvfs': Permission denied* warning.

EDIT: you can press Ctrl+Alt F1 to login in text mode and run the commands. Ctrl+Alt F7 to go back.

---

### Post by Seaniesean on 2008-06-20
Hoorah, posting from ubuntu!  i missed out half of what the earlier helpful chap told me, so that might have worked.

But i did:

sudo chmod 0755 /home

chmod 0644 ~/.dmrc

chmod 700 /home/owner

cd /home

chown owner /home/owner

chgrp owner /home/owner

I think.  Someone tell me if i just gave remote access to my desktop or something.  Honestly, you linux people leave out loads of syntax in your replies sometimes(not sisco, though) assuming that linux cretins like myself are going to fill in the blanks!  We need guidance!

Anyway, i don't think i get any errors now, so thank you!

---

