---
title: "Virtualbox installation"
date: 2009-01-24
forum: General Help
---

### Post by deondebbie on 2009-01-24
Hi All

Im having major problems installing virtualbox-2.1_2.1.2-41885_ubuntu_intrepid_i138.deb,
Im being honest to say that i dont know what commands or what to do to make or compile and extract the files,alot of help will be great,Im using Ubuntu 8.1 intrepid,also i dont have a internet connection for linux,because i cant get my iburst wireless desktop modem to work

Thanxs

---

### Post by howefield on 2009-01-24
You should only need to double click the .deb file that you have downloaded, and the package manager will kick in and take care of the install.

Are you upgrading virtualbox or is this a new install ?

---

### Post by cosine352 on 2009-01-24
or you can just type this command in the terminal

> sudo apt-get install virtualbox

you can open the terminal from 

Applications --> accessories --> terminal

---

### Post by deondebbie on 2009-01-25
Its a new installation when I double click the file it shows a error with lbid4

---

### Post by adamlau on 2009-01-25
Likely a dependency issue. If you understand the shortcomings of the cripped OSE version in the repositories, you can simply:

```
sudo apt-get update && sudo apt-get install virtualbox
```

If you insist on using your downloaded version, simply run the following afterwards:

```
dpkg -i /path/to/virtualbox-2.1_2.1.2-41885_ubuntu_intrepid_i138.deb
```

---

### Post by deondebbie on 2009-01-26
The actual error is unsatisfied package libq4-network error

---

