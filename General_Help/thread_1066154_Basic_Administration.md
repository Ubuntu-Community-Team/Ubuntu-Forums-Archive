---
title: "Basic Administration"
date: 2009-02-10
forum: General Help
---

### Post by PrinzPH on 2009-02-10
Hi All. We recently shifted our office computers to Ubuntu (8.04 LTS). We have around 10 systems on it now, with an 'Admin' account, and for normal users we have created 'Unprivileged' accounts. I have a couple of questions on basic administration:

1.) Back when we were still on XP, we used tightvnc for remote administration. It worked great. Now on Ubuntu, we've been doing ok with the built in vnc server, however, we came to 'discover' that we have to configure it with each account (that is, we login under each credential and setup the password and everything else). I was wondering if we could set it to run with our specified settings regardless of which user logs in. (Side note: the built in client on Ubuntu is awesome with its tabs/bookmarks)

2.) On a select few computers, we have to share a folder (on a second, partition, NTFS). We already have Samba installed, I made only 2 changes on /etc/samba/smb.conf (setting: usershare owner only = False, and the host description). Now same case as above, the share only becomes accessible when logged in as our admin account. Does it have anything to do with the fact that when the partition is mounted, admin/sudo privileges are required? We need it to be shared upon boot if possible. And how do we mount that share from other computers on login? How do we make mounts persistent across sessions?

3.) I realize that the menu items on the Panel are customizable, is a way to set the default menu items for unprivileged users (ie no System menu)?

Thanks in Advance

---

