---
title: "Open Office issue with Office 2003 links."
date: 2010-12-16
forum: Desktop Environments
---

### Post by zadex on 2010-12-16
I got the next issue after installing ubuntu desktop on 27 desktops and laptops:

All the links between files on a local samba share are not working anymore for the stations on linux.
A normal vlookup on an excel with windows would look like:
=VLOOKUP(Q833,'smb://192.168.139.2/public/1 rapoarte clienti/KEX/Tip Clienti.xls'#$Sheet1.$A$1:$F$1048576,6,FALSE())

on linux should be something like:
=VLOOKUP(Q833,'/home/usr/.gvfs/public on 192.168.139.2/1 rapoarte clienti/KEX/Tip Clienti.xls'#$Sheet1.$A$1:$F$1048576,6,FALSE())

I need to fix this problem because if i change the lookups it won`t work for the windows users ( which i currently hate :P ).

Any ideeas ?

---

