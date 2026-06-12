---
title: "Completely Reinstalling Compiz in Lucid"
date: 2010-05-29
forum: Desktop Environments
---

### Post by 8181 on 2010-05-29
I've been having a problem with my main user account ever since I installed Lucid where after I enter my login credentials, the desktop always freezes. Since I've been having this problem, I created another user and have been able to login fine with this one. I have determined that the problem is with compiz, so I want to completely reinstall compiz, including any configuration settings. However, there seem to be a number of packages that go with compiz so I'm not sure what steps I can follow to accomplish this. Can anyone tell me the steps I need to take?

---

### Post by hok00age on 2010-05-29
> **8181 said:**
> I've been having a problem with my main user account ever since I installed Lucid where after I enter my login credentials, the desktop always freezes. Since I've been having this problem, I created another user and have been able to login fine with this one. I have determined that the problem is with compiz, so I want to completely reinstall compiz, including any configuration settings. However, there seem to be a number of packages that go with compiz so I'm not sure what steps I can follow to accomplish this. Can anyone tell me the steps I need to take?

Run:
```
sudo apt-get purge compiz*
```
```
cd $HOME && rm -rf .compiz/ .config/compiz/
```
```
sudo add-apt-repository ppa:compiz/ppa && sudo apt-get update
```
```
sudo apt-get upgrade && sudo apt-get install compiz
```

Hope it helps
Regards :)

---

### Post by 8181 on 2010-05-29
Thanks for the quick response hok00age. I followed the steps and it worked for reinstalling compiz... but the login problem persists. I'm not sure what will fix it at this point, but I appreciate your help.

---

### Post by bildr on 2010-05-29
there was a problem with libplymouth that caused this symptom for a while, make sure you are up to date

---

### Post by 8181 on 2010-05-29
> **bildr said:**
> there was a problem with libplymouth that caused this symptom for a while, make sure you are up to date

 Amazing. After many, many hours spent trying to figure out this problem, one little package reinstall fixed everything. Thank you bildr!

---

