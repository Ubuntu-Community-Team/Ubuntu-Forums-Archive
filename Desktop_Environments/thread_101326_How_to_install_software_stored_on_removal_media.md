---
title: "How to install software stored on removal media???"
date: 2005-12-09
forum: Desktop Environments
---

### Post by mabuti on 2005-12-09
I have recently installed Ubuntu 5.10 on my Dell notebook. It runs smoothly, no complaints at all. However, for some reasons, I will not have access from my  notebook to the internet for the coming months or so.  But I wanted to install some softwares like gcc. Is it possible that I download on different computer, save  it on removable storage then install on my notebook from the removable storage? If yes, how do I go about doing that?:confused: 
Help help!!!
Ubuntian:D

---

### Post by aysiu on 2005-12-09
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by mabuti on 2005-12-10
That's fair enough, however non of the computers I will be using to access the internet have linux on them.
Is it possible that I do all that in a windows enviroment??
Ubutian:D

---

### Post by dalee on 2005-12-10
Hi,

You can always download in Windows and save them to what ever media. Then put ithe media into your Linux box, open a terminal, and then simply cd to that directory, then do  "sudo dpkg -i packagename.deb" . That should install it for you.

This will not handle ANY dependencies. So it can be very frustrating and time consuming to find and install all of those seperately.

dalee

---

### Post by Rackerz on 2005-12-10
[QUOTE=dalee]Hi,

You can always download in Windows and save them to what ever media. Then put ithe media into your Linux box, open a terminal, and then simply cd to that directory, then do  "sudo dpkg -i packagename.deb" . That should install it for you.

This will not handle ANY dependencies. So it can be very frustrating and time consuming to find and install all of those seperately.

dalee[/QUOTE]

Yeah that's what i do if ever i can't get a package on while on Ubuntu (which is rare).

---

