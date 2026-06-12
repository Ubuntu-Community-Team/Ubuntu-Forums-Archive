---
title: "post-install root password doesnt work"
date: 2006-01-26
forum: Desktop Environments
---

### Post by Howcomes on 2006-01-26
Ok, so ive just installed Kubuntu 5.10 - first time ive gotten it to work/boot - KDE is loaded and everything more or less is functional.....except the root password doesnt work. The user account i created works, but im sure at some point im going to need root access.

---

### Post by heimo on 2006-01-26
Does this information help?
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

---

### Post by Howcomes on 2006-01-26
[QUOTE=heimo]Does this information help?
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)[/QUOTE]

yes, yes it does. Thx.

I'll repost here for anyone else with this problem.

```

RootSudo

By default, the password for root is locked in Ubuntu. This means you cannot login as root or use su. Instead, the installer will setup sudo to allow the user that is created during install to run all administrative commands.

This means that in the terminal you can use sudo for commands that require root privileges. All programs in the menu will use a graphical sudo to prompt for a password. When sudo asks for a password, it needs YOUR password, this means that a root password is not needed. 

NOTES

    *

      The password is stored by default for 15 minutes. After that time, you will need to enter your password again.
    *

      To run the graphical configuration utilities with sudo, simply launch the application via the menu.
    *

      To run a program using sudo that normally is run as the user, such as gedit, go to Applications --> Run Application and enter gksudo gedit.
    *

      For users of Kubuntu, use kdesu in replacement for gksudo.
    *

      Ubuntu 5.10 (Breezy Badger) users, go to Applications --> System Tools --> Run as different user.
    *

      To use sudo on the command line, preface the command with sudo, as below:

Example #1

sudo chown bob *

Example #2

sudo /etc/init.d/networking restart

    *

      NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail.
    *

      To start a root shell (i.e. a command window where you can run root commands) use:

sudo -i

```

Nice work (K)Ubuntu on disabling root. and thx Heimo for the tip.

---

### Post by bulldogzerofive on 2006-01-26
I wish I had read that before!  I was wondering why sudo kept screwing up config file ownership... so i need to use kdesu!  I had no idea!

---

