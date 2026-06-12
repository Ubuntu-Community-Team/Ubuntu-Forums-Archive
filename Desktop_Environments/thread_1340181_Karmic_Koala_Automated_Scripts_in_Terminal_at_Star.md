---
title: "Karmic Koala: Automated Scripts in Terminal at Startup?"
date: 2009-11-28
forum: Desktop Environments
---

### Post by vince.lupe on 2009-11-28
Hi, everyone,

Is there a way to get the terminal to script:

[I]vince@vince-laptop:~$ sudo apt-get update
vince@vince-laptop:~$ sudo apt-get dist-upgrade
     ~~~~~~~~~~~~~~~
              ~~~~~~~~~~~~~~ [Y/n] [/I](Yes, I'd like to upgrade)
[I]vince@vince-laptop:~$ sudo apt-get upgrade
[/I][I]~~~~~~~~~~~~~~~
              ~~~~~~~~~~~~~~ [Y/n] [/I](Yes, I'd like to upgrade)
*vince@vince-laptop:~$* *sudo apt-get autoclean*
[I]vince@vince-laptop:~$ sudo apt-get autoremove
[/I][I]~~~~~~~~~~~~~~~
              ~~~~~~~~~~~~~~ [Y/n] [/I](Yes, I'd like to upgrade)

at startup?

I hate having to take the time to do this every time that there is an upgrade. Thank you, ya'll! God bless!

- Vince

---

### Post by scorp123 on 2009-11-28
The update manager should check for updates automatically? And if you don't want to be bothered about manually updating stuff you could install Ubuntu Server's "**unattended-upgrades**" package. It's in the repos and works on the desktop edition too and it does all the update magic all by itself.

If you still insist on adding those commands to your **~/.bashrc** or **~/.profile** without being asked a password, you should add yourself to the **/etc/sudoers** file and add those commands with the "NOPASSWD" option.

Read here:
[http://ubuntuforums.org/showthread.php?p=8387254#post8387254](http://ubuntuforums.org/showthread.php?p=8387254#post8387254)

---

