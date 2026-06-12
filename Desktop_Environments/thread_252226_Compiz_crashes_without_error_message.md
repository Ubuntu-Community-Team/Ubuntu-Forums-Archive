---
title: "Compiz crashes without error message"
date: 2006-09-06
forum: Desktop Environments
---

### Post by bsander on 2006-09-06
I had XGL/Compiz working fine until I rebooted today. I don't know if it's because of a recent update, but all of a sudden when I start Compiz, X crashes and the only message I see is > X connection to :0.0 broken (explicit kill or server shutdown).

Who can give me a clue as to what the cause (or rather, the solution ;) ) may be?

---

### Post by bulldog on 2006-09-06
this is because compiz relies on csm instead of gconf now...
so you must start compiz differently, basically...

go to system -> prefs -> sessions -> startup programs and put in "/usr/bin/compiz-start"

EDIT:after today's update just then, /usr/share/compiz-start doesn't work for me anymore, so if it doesn't work for you, put in "compiz-start --replcae" instead...

(instead of whatever you use to start compiz currently)

also make sure you have "csm" installed and all other packages are upto-date....



then run "csm" in the terminal to change any of the settings for any plugin....

if changes in csm don't have any effect, then go into the terminal and type "sudo chmod 755 ~/.compiz -R"
if it complains about a folder being missing, then create a ".compiz" folder in ur home folder and run the command again....

then it should all work again....


This is copied from the compiz forum and works for me,hope for you too.

---

### Post by bsander on 2006-09-07
Thanks, you got me i the right direction, turned out cgwd was not installed for some reason. It's all working fine now :)

---

