---
title: "Visual Novel Game (*.sh) can not execute"
date: 2015-08-03
forum: Gaming &amp; Leisure
---

### Post by SOSESU on 2015-08-03
Sorry. I have some problem to excute .sh file and other visual novel,
When I am execute sh file from visual novel
"/lib/python: Permission denied"
I have done chmod or give permission to sh file, but I can resolve my problem. can you help me?

---

### Post by MikeCyber on 2015-08-03
michael@michael-ubuntu:/$ whereis python
python: /usr/bin/python3.4 /usr/bin/python2.6 /usr/bin/python2.6-config /usr/bin/python2.7 /usr/bin/python2.7-config /usr/bin/python3.4m /usr/bin/python2.6-dbg /usr/bin/python2.6-dbg-config /usr/bin/python /usr/lib/python3.4 /usr/lib/python2.6 /usr/lib/python2.7 /etc/python3.4 /etc/python2.6 /etc/python2.7 /etc/python /usr/local/lib/python3.4 /usr/local/lib/python2.6 /usr/local/lib/python2.7 /usr/include/python2.6 /usr/include/python2.6_d /usr/include/python2.7 /usr/include/python3.4m /usr/share/python /usr/share/man/man1/python.1.gz
michael@michael-ubuntu:/$ which python
/usr/bin/python
michael@michael-ubuntu:/$ 

That's what I get on 15.04. If you have python installed it probably wants a link to /lib/python. Tell the dev. to fix and meanwhile do:
sudo ln -s /usr/lib/python3.4 /lib/python

---

### Post by SOSESU on 2015-08-03
> **MikeCyber said:**
> michael@michael-ubuntu:/$ whereis python
python: /usr/bin/python3.4 /usr/bin/python2.6 /usr/bin/python2.6-config /usr/bin/python2.7 /usr/bin/python2.7-config /usr/bin/python3.4m /usr/bin/python2.6-dbg /usr/bin/python2.6-dbg-config /usr/bin/python /usr/lib/python3.4 /usr/lib/python2.6 /usr/lib/python2.7 /etc/python3.4 /etc/python2.6 /etc/python2.7 /etc/python /usr/local/lib/python3.4 /usr/local/lib/python2.6 /usr/local/lib/python2.7 /usr/include/python2.6 /usr/include/python2.6_d /usr/include/python2.7 /usr/include/python3.4m /usr/share/python /usr/share/man/man1/python.1.gz
michael@michael-ubuntu:/$ which python
/usr/bin/python
michael@michael-ubuntu:/$ 

That's what I get on 15.04. If you have python installed it probably wants a link to /lib/python. Tell the dev. to fix and meanwhile do:
sudo ln -s /usr/lib/python3.4 /lib/python
I use python 2.7.6 on Xubuntu 14.04

---

### Post by Sslaxx on 2015-08-04
Ren'Py should come with its own Python libraries. You may want to go talk about it on their forums too.

---

