---
title: "big problem in ubuntu 9.04"
date: 2009-06-20
forum: General Help
---

### Post by al prince nofl on 2009-06-20
Hey

i have a problem with my system, that's not the first one.

the [IMG]file:///tmp/moz-screenshot.jpg[/IMG]screenshot  will show:

[IMG]http://omarnofl.com/other/Screenshot-error.png[/IMG]

Please Help

---

### Post by drs305 on 2009-06-20
You have one or more corrupted files in /var/lib/apt/lists. The easiest way, in case there are multiple corrupted files, is to just recreate the entire list:
```

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old  # rename existing list folders
sudo mkdir /var/lib/apt/lists /var/lib/apt/lists/partial  # create empty folders
sudo apt-get update  # update the lists

```

If everything is fixed, you can use nautilus to remove the old list folder:
```

gksudo nautilus /var/lib/apt

```
Use SHIFT-DELETE to remove the "lists.old" folder (including its subfolders).

---

### Post by al prince nofl on 2009-06-20
Thanks, but i cant rename or creat any file !!

May be because i am not the root, i have the root password but i don't know how to login as root.

---

### Post by drs305 on 2009-06-20
If you are part of the "admin" group you would simply type in your password when asked. You won't see it as you type but it will be registered. Hit ENTER when you have typed it in. You don't have to "log in" to temporarily gain root privileges *if* you are a member of "admin".

If you aren't sure if you are in the "admin" group, you can type this to see. If you are, you will see "admin" listed:
```
groups
```

---

### Post by al prince nofl on 2009-06-20
> **drs305 said:**
> If you are part of the "admin" group you would simply type in your password when asked. You won't see it as you type but it will be registered. Hit ENTER when you have typed it in. You don't have to "log in" to temporarily gain root privileges *if* you are a member of "admin".

If you aren't sure if you are in the "admin" group, you can type this to see. If you are, you will see "admin" listed:
```
groups
```

Where i can do that ?

Is it from the login screen ?

---

### Post by drs305 on 2009-06-20
> **al prince nofl said:**
> Iam sorry,  But where i can do that ?

Is it on the login screen ?

No, you do that from a terminal: Applications, Accessories, Terminal.

---

### Post by al prince nofl on 2009-06-20
Thanks

---

