---
title: "Default Menu Items"
date: 2007-07-16
forum: Desktop Environments
---

### Post by masterr on 2007-07-16
I am setting up a few oem systems with Ubuntu. I want to install a few extra programs for the end user than what the default Ubuntu install has, but I have run into a couple programs that do not set up icons in the application menu. This is easy enough to add manually, but my problem is that I do not know of a way to have these show up by default for all new users.

Can anyone point me in the right direction on how to change the default entries. It seems that the included editor (alacarte) doesn't support editing the defaults and I can't find another easy way to do this. I even tried copying ~/.conf/menu/ to /etc/skel and then creating new user but it didn't seem to work.

Maybe I'm not looking in the right spots, so any help would be appreciated.

Thanks

---

### Post by masterr on 2007-07-16
Update for those with the same problem:

I figured it out. I copied an entry from /usr/share/applications and edited it for the program I wanted and it worked.

---

