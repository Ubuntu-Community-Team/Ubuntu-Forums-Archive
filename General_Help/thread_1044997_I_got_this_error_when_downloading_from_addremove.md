---
title: "I got this error when downloading from add/remove"
date: 2009-01-20
forum: General Help
---

### Post by joelr2005 on 2009-01-20
Hello everyone this is my first time posting to the forum. I am a new-bi and decided to try wubi and installed it now I have ubuntu 8.10. I did all updates and when I went to download software from the repository and I check off all the software that I was interested in. As they were downloading my pc froze and i had to restart holding the power button . i than powered up my pc. After boot i noticed that half of the software that I"ve requested did not download so I decided go back and download the software.I check off the software I want agian and i got this error.



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


Anyones help will be appreciated.

---

### Post by kostkon on 2009-01-20
Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give
```
sudo dpkg --configure -a
```
it will ask you for a password, give yours.

After doing the above, you can try again to use Add/Remove to install the programs you want.

---

### Post by joelr2005 on 2009-01-20
thank you for the help.

---

