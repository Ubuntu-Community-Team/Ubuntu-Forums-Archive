---
title: "Where to set compose key in Xubuntu 11.10"
date: 2011-11-14
forum: Desktop Environments
---

### Post by Paulr-55 on 2011-11-14
Sorry, but I've searched and can find no clue. The keyboard settings dialog does not give access to the layout details like in Ubuntu. Is there a configuration file somewhere?

Xubuntu 11.10 on a System 76 Ratel desktop.

—update

I find that the command:

$ xmodmap -e "keysym Alt_R = Multi_key"

Sets the right Alt key as the compose trigger. I have spent half a day now trying to get that executed at startup but to no avail. I put it in a bash script and added it to my apps startup list: did not work. Added the command to my .bashrc : nothing. Will continue my search...

—Update

Got it. Put the xmodmap commands in a file called ~/.Xmodmap and this will be run on startup by the system.

---

### Post by Ghost_Mazal on 2012-03-02
This doesn't work. Anybody know another way to set the compose key in xubuntu ?

---

### Post by Toz on 2012-03-03
According to [https://help.ubuntu.com/community/ComposeKey]("https://help.ubuntu.com/community/ComposeKey"), for 8.10, there is a XKBOPTIONS= setting in /etc/default/console-setup. On my 11.10 system, this parameter is now found in /etc/default/keyboard.

---

### Post by Ghost_Mazal on 2012-03-03
> **Toz said:**
> According to [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey), for 8.10, there is a XKBOPTIONS= setting in /etc/default/console-setup. On my 11.10 system, this parameter is now found in /etc/default/keyboard.

Thank you !! :)

---

