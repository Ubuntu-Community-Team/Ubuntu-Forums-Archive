---
title: "GPG error when updating add/remove applications list"
date: 2009-04-08
forum: General Help
---

### Post by tropnevad on 2009-04-08
I get the following GPG error when trying to update the add/remove programs list.

I have just installed a clean version of ubuntu 8.10 today and dont konw why i am getting this error.. please help

> 
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
thanks

edit: i have been searching the forums and tried a few things like
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
sudo apt-get update

but that never worked either

---

### Post by tropnevad on 2009-04-08
I solved my problem by running the following command

> sudo apt-get update -o Acquire::http::No-Cache=true

hope this can help anyone who is in my situation! :)

---

