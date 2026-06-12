---
title: "User and group permissions on shares"
date: 2006-02-09
forum: Desktop Environments
---

### Post by 5hane on 2006-02-09
I have a file server on a windows network. Is there a way to give one group write access and another read only access to the same share. I am having much difficulty trying to set this up. Any help will be appreciated.

---

### Post by 5hane on 2006-07-03
Open the Samba configuration file: 

  sudo gedit /etc/samba/smb.conf

include the line:

  read list user1

The user "user1" will only have read access. You may add more users, e.g.

  read list user1 user2 user3

The configuration file should then look something like this:

[sharename]
path = sharepath
**read list user1**

---

