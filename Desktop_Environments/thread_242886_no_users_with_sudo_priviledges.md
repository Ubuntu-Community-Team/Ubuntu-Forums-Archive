---
title: "no users with sudo priviledges"
date: 2006-08-24
forum: Desktop Environments
---

### Post by 944jon on 2006-08-24
I installed 6.06 using the alternate cd and installed updates and everything else I need using automatix. I ran oem-config-install and now I don't have any users with sudoer priviledges! I have been able to sudo with the new user on other installations. I don't know what I did differently this time. Is there any way to gain sudo rights or do I have to reinstall everything?

Is there any way to add the existing user to the admin group without a sudoer? maybe run the live cd and do this?

I though someone else must have had this problem but I did not find any other threads.](*,)

---

### Post by FuriousLettuce on 2006-08-24
When you reboot, press [ESC] (the key) to load up the GRUB menu, then choose 'recovery'. This should log you in as root. To confirm this, open the terminal and type

```
whoami
```

Next, do
```
nano /etc/sudoers
```

and add the line
```
username ALL=(ALL) ALL
```

[Where username is the username you want to have sudo privileges]

Next, press Ctrl+X and make sure you choose to save it.. If there is a line beginning %group, or something along that line, you that means that the user group with the name 'group' has the ability to use sudo, and you can simply add yourself to that group by doing:

```
usermod -g group username
```

---

### Post by 944jon on 2006-08-24
Thanks I knew there was an easy solution I just wasn't thinking of. I am still missing some menu items under System > Administration. Users and Groups, Networking, and Synaptic. I can run these apps from a terminal using sudo. Is there an easy way to reset the menus back to the originals.

---

