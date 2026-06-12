---
title: "shotwell publish function &amp; online accounts"
date: 2014-03-16
forum: Desktop Environments
---

### Post by Mr5o1 on 2014-03-16
Hi all,

Recently installed lubuntu on my gf's laptop and would love to be able to use the shotwell "publish" feature. But there's some problem with online accounts or something?

[LIST]
[*]It's a fresh install of lubu 13.10 on an Acer Aspire D255
[*]I basically get the behaviour described [in this bug report]("http://redmine.yorba.org/issues/6218").
[*]This [ask ubuntu question]("http://askubuntu.com/questions/215249/xubuntu-upload-photos-to-facebook-or-picasa-via-shotwell") seems to say it's a shotwell 0.13 issue, which was resolved in 0.14
[*]current version in the ubu repositories is 0.15, which is what I have installed.
[*]I read [here]("http://askubuntu.com/questions/202514/how-can-i-manage-empathy-online-accounts-in-lubuntu-12-10") that you can install gnome-control-center and run something like "gnome-control-center online-accounts" but I tried that and I don't get any information about online-accounts, there's only three unrelated items. That was a work around for lubu 12.10 anyway.
[/LIST]

The way I see it I have two options: 

first I can figure out how to configure online accounts in lubuntu. Seems like it should be easy but I'm stumped, any help here appreciated.
or option 2: try installing shotwell from their ppa rather than the ubuntu repos. I guess that involves pinning the package in sources.list or some such? It would take me some figuring out, and I'm not sure it would solve my problem.

Thanks in advance for your help.

---

### Post by Mr5o1 on 2014-03-17
I tried a bunch of things to get this working.. but in the end I couldn't get ubuntu online accounts configured correctly.

I reinstalled shotwell from the yorba/ppa - that version has it's own online accounts auth plugins which work fine.

---

