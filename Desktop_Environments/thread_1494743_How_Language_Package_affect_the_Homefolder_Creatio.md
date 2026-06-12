---
title: "How Language Package affect the Homefolder Creation"
date: 2010-05-27
forum: Desktop Environments
---

### Post by volvolinux on 2010-05-27
Hi

I am using Chinese Interface on Ubuntu. I use run-parts to run some login scripts.

In English version the Desktop directory will be /users/Myname/[COLOR=Red]Desktop[/COLOR]
In Chinese version the Desktop Directory will be replaced by Chinese words, that will be /users/Myname/[COLOR=Red]&#26700;&#38754;[/COLOR]

My Script will first to see if there is a file called [COLOR=Red].existcheck[/COLOR] in the folder "[COLOR=Red]&#26700;&#38754;" , [COLOR=Black]if it doesn't exist, it will try to create some files and create the file [COLOR=Red].existcheck [/COLOR], if it exists, it will do nothing.

The Script works well except when the user login during the first time. From what I understand the system will copy files in the /etc/skel during a first login, is there some procedure affect the scripts running during the first login? I mean the first login the Desktop is Desktop not [/COLOR][/COLOR][COLOR=Red]&#26700;&#38754;...[COLOR=Black]

Can some guy help on this?
[/COLOR][/COLOR]

---

