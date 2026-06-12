---
title: "Changed Root Password But Doesn't Stay"
date: 2005-10-26
forum: Desktop Environments
---

### Post by xeero on 2005-10-26
Hello all,

I'd like to have a different "root password" from my own password that I use when I log on with my regular login (i.e., when I log on as myself with my own password, I want Ubuntu to require a different "root" password when I want to run Synaptic).  

I first tried to change the root password using System > Administration > Users and Groups.  However, I seemed to have to change the shell root password separately, because it still required my own user password to sudo.  So at the shell I did "sudo passwd root" and changed it.  

The shell password seemed to stay changed, but the "gui" root password (i.e., the one to run System > Administration > Synaptic Package Manager) keeps going back to my user password.  

I don't know why... Any suggestions?

---

### Post by soul_rebel on 2005-10-26
that's because ubuntu uses gksudo to get root powers and to ask you the pass with a small graphical window. 
That's how ubuntu works. Root is supposed to be disabled.
if you want to use gksu and be asked for root's password instead of your own, you may alternatively change a lot of .desktop files, do some ugly symlink hack or get another distro, perhaps debian.
bye

---

