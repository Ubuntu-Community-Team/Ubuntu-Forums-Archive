---
title: "LyX spell checker"
date: 2012-02-22
forum: Desktop Environments
---

### Post by Pengwyn44 on 2012-02-22
I am using LyX on Ubuntu 11.10 but the spell checker is greyed out.
I have tried to activate it using the Tools --> Preferences Menu. All that happens is the word "ENCHANT" appears, but it will not APPLY or SAVE.

All packages have been downloaded from the Ubuntu Repositories using the Software Centre.  I have used LyX before with the spell checker on earlier releases. I expect that there is a simple solution, but I need someone to supply it. Thanks in advance!


Pengwyn44

---

### Post by venik212 on 2012-02-25
I have the very same problem-- Texlive, Lubuntu 11.10, and no Enchant.... It disappears after a brief appearance in the window.

---

### Post by Pengwyn44 on 2012-02-26
Since writing the above question I have another computer running 11.04, so I used the Software Centre to download LyX. The spellchecker works!
The difference is that 11.04 downloads version 1.6.7. 11.10 downloads version 2.0.0.
So the easy solution is to download the older version onto 11.10, but there is no facility to do so with my limited knowledge.

Expert help is needed!

Pengwyn44

---

### Post by Pengwyn44 on 2012-06-20
I have now got the answer to this problem from the LinuxFormat Forum.
Check in the Software Centre to see if ENCHANT is installed. If not, install it.
Then start Lyx,select TOOLS, PREFERENCES, LANGUAGE SETTINGS, SPELLCHECKER.
Then at SPELLCHECKER ENGINE, select ENCHANT, press ENTER KEY, and click on SAVE.

You should now have a spell checker!

---

### Post by ugm6hr on 2013-02-17
Old thread, but just found on Google. My solution for 12.04:
Enchant is probably already installed, but just in case:
```
sudo apt-get install enchant
```
Then as per above advice to activate.

---

