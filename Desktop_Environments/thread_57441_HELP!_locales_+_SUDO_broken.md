---
title: "HELP! locales + SUDO broken"
date: 2005-08-16
forum: Desktop Environments
---

### Post by mozz on 2005-08-16
Hi,

sry I have to make another thread because now **nothing** is working anymore  :-# 

I did that dpkg-reconfigure locales and when I rebooted ubuntu didn't accept my sudo password?

Here are the facts: The passwords for sudo and my main user are *exactly* the same, but ubuntu only accepts it only at the main login screen for the user not for the sudo command at the shell.

Most things are german (as they were) like Gnome but some, like error messages in the shell or "Enter Password" windows are english

Here's my locales
> LANG=de_AT
LC_CTYPE="de_AT"
LC_NUMERIC="de_AT"
LC_TIME="de_AT"
LC_COLLATE="de_AT"
LC_MONETARY="de_AT"
LC_MESSAGES="de_AT"
LC_PAPER="de_AT"
LC_NAME="de_AT"
LC_ADDRESS="de_AT"
LC_TELEPHONE="de_AT"
LC_MEASUREMENT="de_AT"
LC_IDENTIFICATION="de_AT"
LC_ALL= 

I really don't know what to do, I'm caught in my own 4 walls...can't even get the backups because restoring them needs sudo :(

HELP ME PLEASE!

---

### Post by mozz on 2005-08-16
Sry guys, I'm so done...forgot something:

Ubuntu accepts the password for the main user at the login screen (graphical) but as it seems not at the console :(

Think I have to mention, that my password has characters, figures and special chars in it, so I guess the keyboard layout might be messed up?

---

### Post by Gerie Langeveld on 2005-08-16
It seems that the special characters in your password are a problem.
Type the following first:
export LANG=C
then try sudo. It resets your locale temporarily.

If that doesn't help, try typing your password at the prompt (like a command) and try to find out which character gives the problem.

Also you could try System-->Preferences-->Keyboard and check the keyboard-layout. Is it also German? Are 'dead-keys' enabled?

---

