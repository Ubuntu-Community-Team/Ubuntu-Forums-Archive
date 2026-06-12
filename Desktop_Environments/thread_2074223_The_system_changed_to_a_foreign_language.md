---
title: "The system changed to a foreign language"
date: 2012-10-21
forum: Desktop Environments
---

### Post by jozmak on 2012-10-21
Hi,

I've been using gnome remix without a problem since three days.
But today a very strange thing happened. After logging in every text appeared in chinese or other sign language. And I get a message something like this: you have decided to log in another language. Do you want to change the folder names or keep the old name? Whatever, I do everything appears in chinese. Now my destop is useless, because I don't understand it. I haven't done anything. Yesterday night, I shut down the machine as usual and after switching on the computer this mornign this is what happened to me. How can I go back to English?
Please help.

---

### Post by delqhi on 2012-10-21
does the shell/terminal also change into chinese? if it's not, drop to shell/terminal (ctrl+alt+F1) then do some google.

[this one for example]("http://askubuntu.com/questions/132347/gnome-classic-language-turned-into-chinese-how-do-i-change-it-back-to-english"), it said that
```
sudo pico /etc/default/locale
```
will solve the problem. i do not change anything in that file, do not want end up in your situation. but in my locale file, the only line exist is this:

```
LANG="en_GB.UTF-8"
```

i use elinks or links (sudo apt-get install elinks links) to browsing during emergency from shell, i'm trying to reduce my need for fancy GUI.

to get back to desktop environment, press alt+F7 (or ctrl+alt+F7, just in case).

---

### Post by jozmak on 2012-10-21
Thanks.

```
/etc/default/locale
``` file was properly set. However, the ```
~/.pam_environment
``` file  language setting was in Chinese. I changed that back into English and now, everything works fine in English.

But it still mystifies me how ```
~/.pam_environment
``` got changed into Chinese.

---

### Post by Mr.JJ on 2012-10-21
Most probably you accessed languages and settings (say to change keyboard layout etc.) and this select chinese by default even if your current language is a different one. The settings will take effect only after you restart. 

Please see my bug report [https://bugzilla.gnome.org/show_bug.cgi?id=686493](https://bugzilla.gnome.org/show_bug.cgi?id=686493). Please leave a comment there, that will force the developers to take notice.

---

