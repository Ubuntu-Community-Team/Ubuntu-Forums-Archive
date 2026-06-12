---
title: "scim problem intrepid"
date: 2009-06-01
forum: General Help
---

### Post by namluc on 2009-06-01
Hello, for some reason my chinese input method under scim has disapeared, i was using "zhineng pinyin."  I am left with all of the ones that don't use pinyin (ziranma, wubihua, erbi). i have used sudo aptitude remove and install to restart scim, but that made no difference. where has it gone?? And more importantly how can i get it back?

thanks a lot in advance for your help

---

### Post by Irihapeti on 2009-06-04
It sounds to me as though the scim-pinyin file has developed a problem. Reinstall scim-pinyin, adjust the settings if necessary, and see if that helps.

---

### Post by kalaka on 2009-07-18
You recently upgraded to a new version of Ubuntu (for ex, Hardy to Intrepid)
This causes a problem with SCIM.
You need to remove the scim configuration folder in your home folder with the following code:
```
rm -r ~/.scim
```
Then logout and login again.

Make sure that you have the respective language support,
Goto System > Administration > Language Support
Select your language package.

---

