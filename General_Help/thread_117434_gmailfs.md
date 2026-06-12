---
title: "gmailfs"
date: 2006-01-14
forum: General Help
---

### Post by nene on 2006-01-14
hi boys, I have a problem with gmailfs, i want to mount gmailfs on /etc/fstab, I configure it, like this:

dev                                            mountpoint  type
/usr/share/gmailfs/gmailfs.py   /mnt/gmail   gmailfs

options                                                       
noauto,username=username,password=password,fsname=name

but when I mount /mnt/gmail, 

nene@robboso:~$ sudo mount /mnt/gmail/
nene@robboso:~$ gmailfs.py:Gmailfs:mountpoint: '/mnt/gmail'
gmailfs.py:Gmailfs:unnamed mount options: ['rw', 'noauto']
gmailfs.py:Gmailfs:named mount options: {'username': 'username@gmail.com', 'password': 'password', 'fsname': 'name'}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure

how to fix??
th, and sorry for my bad english.

---

