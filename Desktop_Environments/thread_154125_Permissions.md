---
title: "Permissions"
date: 2006-04-02
forum: Desktop Environments
---

### Post by Digidiz on 2006-04-02
how do i edit permission for a file that i want to edit. the file that i want to edit is rcS.d because the clock is affecting windows clock system

---

### Post by Ramses de Norre on 2006-04-02
sudo chmod xxx path_to_file
The first x are the permissions for the owner, the second for the owner's group, the third for anybody else.
1=x (executable)
2=w (writable)
4=r (readable)
And just add the numbers of the permissions you want to give.

---

### Post by Digidiz on 2006-04-02
yea ok i will try that

---

### Post by Digidiz on 2006-04-02
how do i make it read n writable for all groups i tried to use this command, but it made it only writable, but still not editable, sudo chmod 222 rcS. i went to the folder /etc/default instead of using sudo chmod xxx /etc/default

---

### Post by Ramses de Norre on 2006-04-02
2=writable
6=read-&writable
So chmod 666 will make it rw to everyone, but x to no one.

---

### Post by Digidiz on 2006-04-02
cheers

---

### Post by Digidiz on 2006-04-04
still not working

---

### Post by Ramses de Norre on 2006-04-11
You did the sudo chmod 666 file_name ?
What's the output of ls -a for that file?

Reading your first post again, I guess you should edit it using sudo. Do sudo gedit file_name and type in your user password.

---

### Post by Digidiz on 2006-04-11
i did use sudo gedit file_name to edit a file that wasnt able to be edited by using the text editor

---

