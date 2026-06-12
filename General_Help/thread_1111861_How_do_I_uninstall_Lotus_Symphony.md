---
title: "How do I uninstall Lotus Symphony?"
date: 2009-03-31
forum: General Help
---

### Post by cottfcfan on 2009-03-31
Might seem a silly question.
I installed Lotus Symphony last night, to test against Open Office.
IMO its a poor second, so I went to uninstall it, then realised I couldn`t.
Its not in Synaptic, so i guess i could uninstall it from terminal, but dont know the package name to delete it.
Can anyone help?

---

### Post by sekinto on 2009-03-31
Did you install it from an executable binary? If you did check the directory you installed it in for an uninstall script/program.

---

### Post by cottfcfan on 2009-03-31
Hi sekinto

I installed it as a deb package from the IBM Site.
Ive searched the folder in my home folder but cant find a way to uninstall it.

---

### Post by vibra on 2009-05-30
Open a terminal and type:
sudo apt-get purge symphony

Or

Run synaptic package manager and uninstall it from there.

---

### Post by randancing on 2009-10-26
I want to thank you for the information. I downloaded symphony after reading about it on a web site. I used the synaptic package manager because ubuntu advised it. I didn't care for it so I thought I would just use the add-remove function, but, It was not listed and I was feeling stuck.

thanks again.

---

### Post by P4man on 2009-10-26
another way of removing apps you didnt install from the repo's, is using the janitor in system > administration. Be careful though it seems quite enthusiastic about removing a lot of stuff you probable dont want to remove.

BTW, I kinda like symphony, but to each their own :)

---

### Post by msilvagarcia on 2010-11-22
I was struggling to uninstall it too a while ago, and decided to do it at a later point. Today, I went to IBM's website and found how to uninstall.

```
sudo dpkg -P symphony
```

From here: [http://symphony.lotus.com/software/lotus/symphony/help.nsf/InstallGuide?OpenForm&version=1.1%20Ubuntu%20Beta#4447]("http://symphony.lotus.com/software/lotus/symphony/help.nsf/InstallGuide?OpenForm&version=1.1%20Ubuntu%20Beta#4447")

Hope it helps. :)

---

### Post by kvalvik01 on 2011-02-21
> **randancing said:**
> I want to thank you for the information. I downloaded symphony after reading about it on a web site. I used the synaptic package manager because ubuntu advised it. I didn't care for it so I thought I would just use the add-remove function, but, It was not listed and I was feeling stuck.

thanks again.

Thank you from here, too, same reason to install Symphony, same assessment, same problem getting rid of it

TY

---

