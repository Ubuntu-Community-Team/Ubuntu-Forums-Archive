---
title: "[H]How to move Ubuntu Thunderbird/Evolution to Windows Thunderbird"
date: 2009-05-26
forum: General Help
---

### Post by rofflesupplecake on 2009-05-26
Hi, I would like to return to windows, but keep all my mail intact, I do not have any files or emails deposited in the windows mail and Evolution/Thunderbird automatically delete emails, so is there any way to send my emails in Ubuntu to windows? And how do I access the program files for Ubuntu on windows. Thanks.

---

### Post by pro003 on 2009-05-26
actually, here's a nice tip of [how to]("http://www.freeemailtutorials.com/mozillaThunderbird/backupRestore.cwd")

---

### Post by neur0 on 2009-05-26
For thunderbird:
You just need to copy your whole profile from linux to windows
[http://www.mozilla.org/support/thunderbird/faq#export](http://www.mozilla.org/support/thunderbird/faq#export)
Note that on Ubuntu your profile folder will be located in the .mozilla-thunderbird directory (hidden directory in your home folder, use ctrl-H to see hidden files in nautilus)

Also note that you might have to change your profiles.ini file in windows because of the way windows handles EOL characters. In my opinion, the best way to do this is to create a profile in windows, copy the #######.default folder from the linux profile folder to the windows profile folder and edit the profiles.ini file in the profile folder on windows to point to the new ######.default folder you copied.

For evolution, I don't know

---

