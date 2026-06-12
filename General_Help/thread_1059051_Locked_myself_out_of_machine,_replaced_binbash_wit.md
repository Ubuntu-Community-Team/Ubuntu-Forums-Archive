---
title: "Locked myself out of machine, replaced /bin/bash with /usr/bin/mutt"
date: 2009-02-03
forum: General Help
---

### Post by ensnare on 2009-02-03
I was trying to make it so when I ssh'd into my machine, mutt would automatically launch.  I succeeded in doing that.  Except now, I can't ssh into my machine and do anything else except open mutt.  This user was the only user in the sudo group.  Any ideas on how I can get into my machine ?  Is there a "shell-mode" or something I can enter into from mutt, like there is in vim?  

Thank you.

---

### Post by taurus on 2009-02-03
I am not sure why you want to replace your login shell with a mutt mailing program.  If you want to start mutt when you log in, why not just add it to your ~/.bashrc?

---

### Post by ensnare on 2009-02-03
What I meant was, in /etc/passwd I replaced the shell for my user with /usr/bin/mutt ... which in and of itself wasn't the best idea :-\.

---

### Post by taurus on 2009-02-03
You just have to boot into recovery mode and change your login shell from /usr/bin/mutt back to /bin/bash in /etc/passwd.  Otherwise, you can do that with the LiveCD.

---

### Post by ensnare on 2009-02-03
Hi -- thanks for the quick response.  Is there any way I can do this remotely since physical access to the machine is difficult?  Thanks !

---

### Post by taurus on 2009-02-03
Unless you have created a password for root and allow root remote login, I don't see how it could be done.  However, if you have another account that has root privilege (can do sudo), then yes.  Otherwise, you need the recovery mode.

---

### Post by ensnare on 2009-02-03
Figured it out ... I can execute commands directly from mutt by typing " ! " ... so I executed " ! /bin/bash" which brought up the shell, where I was able to sudo and edit /etc/passwd.  Thanks very much for the starting points, everything is working now.

Take care.

---

