---
title: "Use sudo again?"
date: 2005-04-15
forum: Desktop Environments
---

### Post by pirast on 2005-04-15
Hi,
I used "sudo passwd root" to have a root password. 

Now I want to use sudo again and no root password.

How can I use sudo again?

Thanks,
Martin

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=pirast]Hi,
I used "sudo passwd root" to have a root password. 

Now I want to use sudo again and no root password.

How can I use sudo again?

Thanks,
Martin[/QUOTE]

You can use sudo whether you have your root password set or not. If you really don't want your root password anymore, try "sudo passwd root" again and hit enter for blank passwords.

---

### Post by pirast on 2005-04-15
Hi again,
I already tested it and it sais the following thing:

> No password supplied  :neutral: 

Any ideas?

Thanks,
Martin

---

### Post by nemin on 2005-04-15
[QUOTE=pirast]Hi,
I used "sudo passwd root" to have a root password. 

Now I want to use sudo again and no root password.

How can I use sudo again?
[/QUOTE]
There must be a "correct" way to do this, but what about deleting the root password hash from /etc/shadow?

---

### Post by pirast on 2005-04-15
[QUOTE=nemin]There must be a "correct" way to do this, but what about deleting the root password hash from /etc/shadow?[/QUOTE]
 Hi,
I thought that I can change it, too.

But I need my system and it wouldn't be nice when I can't use root access anymore.

I hope anybody knows the correct way :-)

Thanks for your posting,
Martin

---

### Post by Stormy Eyes on 2005-04-15
Pirast, you can *still use sudo* even if you have a root password set. I used to do it all the time on Gentoo, and I do it all the time on Ubuntu. I use sudo when I want to run one command or run an admin GUI, and I use su to become root in a terminal when I'm going to be doing a lot of work with root privileges.

---

### Post by pirast on 2005-04-15
Hi again,
that's my problem why I want to change again.

Sudo doesn't work. I upgraded from warty. There sudo didn't work after I changed to use a root password. The message was > Sorry, try again. but the password was right.

Now I upgraded to hoary. And there is the same problem. Because I am interested in opening the programs over the gnome menu and not interested in opening the programs over the console, I want to use sudo without password again so I can open the configuration programs over the gnome menu.  :) 

Martin 
PS: Sorry for my bad English...  :|

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=pirast]Sudo doesn't work. I upgraded from warty. There sudo didn't work after I changed to use a root password. The message was  but the password was right.[/QUOTE]

Do me a favor and post the contents of **/etc/sudoers**, please? That's the config file that controls who can use sudo and who can't.

---

### Post by pirast on 2005-04-15
:) :

> # sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
martin  ALL=(ALL) ALL


---

### Post by vicayres on 2005-04-15
[QUOTE=pirast]Hi,
I used "sudo passwd root" to have a root password. 

Now I want to use sudo again and no root password.

How can I use sudo again?

Thanks,
Martin[/QUOTE]

sudo passwd -l root

---

### Post by lao_V on 2005-04-15
why don't you just disable root by typing:

 ```
sudo passwd -l root
```

---

### Post by Juergen on 2005-04-15
To me it sounds like you are now trying to use sudo with the root-password.
Don't - sudo still wants your user-pw, even if the root-pw is set.

---

### Post by pirast on 2005-04-15
> sudo passwd -l root 

was the solution. Thank you everybody.

Martin

---

