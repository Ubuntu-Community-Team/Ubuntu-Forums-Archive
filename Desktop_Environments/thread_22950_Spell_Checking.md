---
title: "Spell Checking"
date: 2005-03-30
forum: Desktop Environments
---

### Post by CouchMaster on 2005-03-30
The spelling checker doesn't seem to be working here in Ubuntu/Konqueror.  It works in SuSE, SimplyMEPIS etc. automatically.  Have I missed something?  How do I get it working?

---

### Post by Reb on 2005-03-30
Use aspell -c to check a text file (from the command line). What does that say? 
I had problems with aspell not working on other distros due to a mismatch between the dictionary version and the program version.

---

### Post by CouchMaster on 2005-03-30
Actually it's ISPELL and it works in OpenOffice - just not here.  Anybody?

---

### Post by CouchMaster on 2005-03-31
This did the trick -
apt-get update
apt-get aspell
apt-cache search aspell

Then I changed the default ISPELL to ASPELL and now she's working!

---

### Post by LongTooth on 2005-04-01
I hate to admit it but I one of the worlds worst spellers. And a program like this is just what I could use. I mostly rely on  [www.Spellcheck.net](www.Spellcheck.net). Boy has it saved my bacon on more that one occasion. Just how do I go about enabling it? Seems from the post I'd have to install it. Will it check everything I write or just on OpenOffice? Don't know a thing about Aspell. A site or HowTo would certainly be usefull for me. Thanks.

---

### Post by CouchMaster on 2005-04-01
First I had to make a root account:
sudo passwd root
type your logon PW here
now your new root PW
Confirm

Now logon as root (it wouldn't let me do this in my regular account)
su
PW
apt-get update (this finds the updates)
apt-get install aspell (this installs aspell)
exit
exit

Now go into System > Settings > Spell Checker > Client - here is a drop down box - click aspell and it should change the dictionary as well and thats it...

---

