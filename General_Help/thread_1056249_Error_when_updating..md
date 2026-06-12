---
title: "Error when updating."
date: 2009-01-31
forum: General Help
---

### Post by Dieseler on 2009-01-31
I get this when trying to apply updates with Adept.
Can anyone tell me what is wrong?
I checked the repositories and they appear to be checked as usual.
Have those updates been pulled. I didn't realize when I pasted it in that it would make links to the repos and I get the 404 when I click them from here.

Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: 
APT Error. Context:
    Package download failed, 
    [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.26_amd64.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.26_amd64.deb:) 404 Not Found, 
    [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.26_all.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.26_all.deb:) 404 Not Found, 
    [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.26_amd64.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.26_amd64.deb:) 404 Not Found, 
    [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_amd64.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_amd64.deb:) 404 Not Found

---

### Post by wolfen69 on 2009-01-31
try
```
sudo apt-get update
```
first.

---

### Post by Dieseler on 2009-01-31
Thanks Wolfen.
A few came in and now adept seems to be working its updates to.
I'll be rooting for them Cardinals tomorrow cause they took out my Falcons.

---

