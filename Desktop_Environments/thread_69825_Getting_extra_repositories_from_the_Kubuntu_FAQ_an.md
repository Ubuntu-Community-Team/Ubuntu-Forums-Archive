---
title: "Getting extra repositories from the Kubuntu FAQ and restoring old sources.list file"
date: 2005-09-28
forum: Desktop Environments
---

### Post by bdmp on 2005-09-28
I am using the Kubuntu Unofficial FAQ at [http://kudos.berlios.de/kf/kf1.html](http://kudos.berlios.de/kf/kf1.html)

In the "How to add exra repositories" section it says to "Exit from Kate (or KWrite), saving the sources.list file (that I downloaded from the FAQ) in your working directory, then put it into effect as below:"  It then asks me to do 2 commands. The first is

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.`date +%y%m%d-%H%M`
```

I thought the first file and the second were the same location so I changed the command to

```
sudo mv /home/burepe/desktop/etc/apt/sources.list /etc/apt/sources.list.`date +%y%m%d-%H%M` 
```

and that screwed everything up. Now mysources.list file is empty.

So here are my questions:

1. How to I go about getting back the contents of sources.list? 

Also, I want to add the extra repositories so I can download the stuff I need, but the "how to add extra repositories" [http://kudos.berlios.de/kf/kf1.html](http://kudos.berlios.de/kf/kf1.html)
section on that faq is confusing. It seems that after following the steps on the faq that the 2 files he had me download are still sitting where I downloaded them, one was editied and saved, but I don't understand what he wants me to do?

2. Do you think you could explain what he is talking about?

Thanks in advance.

---

### Post by Paperjam on 2005-09-28
Just save this file as sources.list: [http://ubuntuguide.org/sample/sources.list_extrarepositories]("http://ubuntuguide.org/sample/sources.list_extrarepositories")

---

### Post by bdmp on 2005-09-28
Thanks.

---

