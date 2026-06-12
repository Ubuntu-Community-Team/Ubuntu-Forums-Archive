---
title: "Uninstalling another distro and installing Ubuntu MATE"
date: 2015-04-26
forum: Desktop Environments
---

### Post by Alexander_Mercer on 2015-04-26
Up to this point I had Kali Linux installed on my laptop, however, I want to change it to Ubuntu MATE, because I found it suits better. I know a similar question has been posted a few times, but I want to make sure, that I don't mess up.

Now, to my question. Kali Linux uses GRUB to handle the booting, and as far as I know, Ubuntu doesn't, would that be a conflict for the installation? Or would I have to somehow delete GRUB, and if so, could anyone point it out to me how? Support will be greatly appriciated. Thanks, in advance.

---

### Post by Dennis N on 2015-04-26
Ubuntu does boot using grub. You can replace Kali by installing Ubuntu to the same partition Kali is on - use the "something else" option in the installer to choose a specific partition to install on. No need to delete or uninstall Kali first. The installer in fact will format the chosen partition before unstalling Ubuntu there.

---

