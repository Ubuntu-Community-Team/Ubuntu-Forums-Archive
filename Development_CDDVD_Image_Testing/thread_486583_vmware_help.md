---
title: "vmware help"
date: 2007-06-28
forum: Development CD/DVD Image Testing
---

### Post by ceezax on 2007-06-28
i have downloaded an ubunto desktop image for vmware from this site 

[http://isv-image.ubuntu.com/vmware/](http://isv-image.ubuntu.com/vmware/)

i have downloaded  Ubuntu-6.06.1-desktop-i386.zip 

now i don't have the password for the root account ? they tell in the site that the password is (password)

but i tried it and no way , so don't any body know what is the root password ?

---

### Post by scxtt on 2007-06-28
can you boot it into recovery mode?  hit escape when grub tells you to, should be an option ...

---

### Post by rbmorse on 2007-06-28
Ubuntu doesn't normally allow access to root. 

Use sudo *command* from a terminal or <alt>+<F2> then enter gtksu *command* in the dialog to start a GUI app with temporary root permissions.

When prompted for a password enter the *user* password

---

### Post by ceezax on 2007-06-28
please can you write the command to configure my ethernet ? from the terminal ??

---

### Post by ghost_ryder35 on 2007-07-11
> **ceezax said:**
> i have downloaded an ubunto desktop image for vmware from this site 

[http://isv-image.ubuntu.com/vmware/](http://isv-image.ubuntu.com/vmware/)

i have downloaded  Ubuntu-6.06.1-desktop-i386.zip 

now i don't have the password for the root account ? they tell in the site that the password is (password)

but i tried it and no way , so don't any body know what is the root password ?
root is not allowed access by default.  if you would like local root access login under another user name, go to System, Administration, Login Window, Security (tab), then check local administration login.  Then more than likley you will have to go into System, Administration, Users and Groups, then make a password for the "root" account.

---

