---
title: "How to create folders or put files on desktop in kubuntu 12.04"
date: 2012-07-05
forum: Desktop Environments
---

### Post by Pally1 on 2012-07-05
How do i do that?

---

### Post by msammels on 2012-07-05
Put them in the /home/<user>/Desktop folder.

---

### Post by codemaniac on 2012-07-05
> **Pally1 said:**
> How do i do that?

Open up a terminal , alt+ctrl+T .
In order to make a directory .

```
mkdir /home/***your_username***/Desktop/***dirname***
```

You can cd into it and create files as per your wish .
```
cd /home/***your_username***/Desktop/***dirname***
```

---

### Post by drmrgd on 2012-07-05
As long as you are running something like the "Desktop Icons" activity, you can just simply drag and drop stuff to the desktop.  Right clicking will give you a menu that will allow you to "Create New..." folders and whatnot.  

It is true that you can access and modify these things through the terminal.  However, GUI will work just fine as long as you are using the correct Activity

---

### Post by Ashtechsmith on 2012-07-05
new install of Kubuntu 12.04 64bit.  installed all available updates.  installed Webmin.

created a 'share' within Webmin - /shared/music  (custom created folder)

from my Windows desktop, i can view the network share and (in theory)  its contents.  i cannot add any files to the share though.  i get an  error stating 'access denied.'

i did make certain that the username and password are the same on the Windows desktop, Linux box and within Samba.

i then created another share - /home/joel/Music

again,

---

