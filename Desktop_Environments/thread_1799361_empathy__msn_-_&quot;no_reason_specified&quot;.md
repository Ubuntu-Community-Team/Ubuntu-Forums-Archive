---
title: "empathy / msn - &quot;no reason specified&quot;"
date: 2011-07-07
forum: Desktop Environments
---

### Post by evan54 on 2011-07-07
os used:
Ubuntu 11.04, with classic gnome environment (ie no unity).

I know this has been discussed before but it seems a lot of people are still having problems (including myself).

**Problem:**
[INDENT]Trying to log on to msn through empathy doesn't work. Instead you get the message "No reason specified".
[/INDENT]

**Suggested Solutions (that don't work for me):**
[LIST]
[http://digitizor.com/2010/10/23/how-to-fix-the-msn-bug-in-empathy-ubuntu-10-10/](http://digitizor.com/2010/10/23/how-to-fix-the-msn-bug-in-empathy-ubuntu-10-10/) - Doesn't work as the file already has the correct entry.
[/LIST][LIST]
kill telepathy-butterfly, telepathy-butterfly is not running. When I do **"ps -e | grep tele"** all I get is **telepathy-logge**.
[/LIST]

**Things I know:**
[LIST]
The problem has something to do with the settings in the dot files in the home folder. If I create a fresh user account or move all the dot files to some other location then it all works fine, aside the fact all settings are lost.
[/LIST]

So I guess I'm asking if anyone has any experience with where things are saved related to empathy / msn in the dot files and what the correct set up is.

Relevant files/folders I already know of:
- .gnome2/keyrings/<yourkeyring>.keyring (usually login.keyring)
- .config/Empathy/*
- .cache/telepathy/avatars/butterfly/msn
- .cache/telepathy/logger/sqlite-data
- .mission-control/accounts/accounts.cfg

I guess from here on is where I need help... Anyone have experience with the set up of butterfly and or empathy? Also, should I have telepathy-butterfly running? Maybe that's the problem?

thanks

---

### Post by dimas869 on 2011-07-09
i use msn in empathy on ubuntu 11.04 with not problem at all

so if you want to try a simple way to unistall and remove any history of empathy in your system and the install it again and create  your msn account again

to remove and clear:

[PHP]sudo apt-get --purge remove empathy[/PHP]

to install it again:

[PHP]sudo apt-get install empathy[/PHP]


and i know you can not make voice and video calls on msn as the recently changed their script but if you have a gmail account perhaps then you can but you have to install the extra codecs as they not included in the package but you can find them searching for **sofiasip** in your application manager and install it too


good luck

---

### Post by Ze Grisi on 2011-11-08
I'm having the same problem as evan54 (ubuntu 11.04;unity).
From the Empathy website:
**Where does Empathy save files (accounts, logs, configuration)?**

 
[LIST]
[*]Accounts settings are saved in *.mission-control/accounts/accounts.cfg* (except passwords which are stored in gnome-keyring).
[*]New logs (since Empathy 2.31.4) are saved in *~/.local/share/TpLogger/logs*
[*]Old logs are saved in *~/.local/share/Empathy/logs/*
[*]Empathy configuration is stored in DConf and *~/.config/Empathy/*
[*]Avatars are cached in *~/.cache/telepathy/avatars/*
[*]Metacontact settings (since Empathy 2.32) are located at *~/.local/share/folks/relationships.ini*
[/LIST]

However, I erase all those files, and also try the "purge remove", and after reinstallation Empathy somehow still have may accounts saved data.

---

### Post by hugolia on 2011-11-11
I am having the same issue. In the last 3 or 4 days I cannot log in any MSN accounts. But login to Yahoo or Gmail work fine.
MSN account keeps loging for ever.
Where can I check the error? Is there any log file?

Hugo

---

