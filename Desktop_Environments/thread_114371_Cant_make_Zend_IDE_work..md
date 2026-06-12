---
title: "Cant make Zend IDE work."
date: 2006-01-08
forum: Desktop Environments
---

### Post by leeb on 2006-01-08
I install the Zend Studio on Amd and X86_64 ubuntu.

I found some information on how to make it work , some was in this forum 
none of them work 100%(may be they work but they was too complicated for me), some of them suggest using Chroot (as a n00b user of linux I looked for easy way) and I found this article

[http://www.tenshu.net/archives/2005/06/01/zend-studio-64bitness/](http://www.tenshu.net/archives/2005/06/01/zend-studio-64bitness/)

first I try part one of the article and then after do what it said and no succesing I sow the _update 1 and 2_.

that say use this line 
cat ZendStudio-4_0_2.bin | sed -e 's/=2.2.5/=a.a.a/g' >ZendStudio-4_0_2.bin.1
(that I dont really no what is the diff)

I comment the relavent lines ("export....") that reffer in the article.
well I stop getting anyoing error about gcj or the shared object.

now there is new error:

Unable to locate the application's 'main' class. The class 'com.zend.ide.desktop.Main' must be public and have a 'public static void main(String[])' method. (LAX)
Unable to Launch Java Application: Unable to locate the application's 'main' class. The class 'com.zend.ide.desktop.Main' must be public and have a 'public static void main(String[])' method. (LAX)

I can't figure out whats the problem now.
Can any one drop some light on this issue.

many many thanks for any help.

---

