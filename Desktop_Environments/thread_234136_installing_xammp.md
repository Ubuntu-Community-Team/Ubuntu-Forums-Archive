---
title: "installing xammp"
date: 2006-08-11
forum: Desktop Environments
---

### Post by olking on 2006-08-11
I am trying to install xammp.
I downloaded the file to desktop and then followed the instruction as below except that I used sudo instead of su because I couldnt get su to authenticate.

This was the instruction:-

# Go to a Linux shell and login as the system administrator root:

su

# Extract the downloaded archive file to /opt:

tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

it gave me no such file or directory, so I moved to Desktop and entered ls.
This said that the file is present so I tried again in that directory and got the no such file etc again

I have had the same problem trying to install direct X 9.
I guess I am missing something obvious.
Can anyone help me please?

---

### Post by maniacmusician on 2006-08-11
maybe it's a typo? that's all I can think of. a handy tool to use is to enter the first couple letters of the filename, and then press tab. it will try to fill it in for you.

instead of extracting in terminal, you could probably just double click it and use whatever program opens it to extract to /opt.

---

### Post by olking on 2006-08-14
Hi I did as you suggested--double clicked and installed it in /opt quite happily.
Everything shows in /opt and when I ls it all shows up fine.
Trouble now is that when I give the command /opt/lammp/lammp start
I get no such file or directory.
Any suggestion please

---

