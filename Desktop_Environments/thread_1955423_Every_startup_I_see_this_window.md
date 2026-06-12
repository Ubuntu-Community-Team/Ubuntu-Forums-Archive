---
title: "Every startup I see this window"
date: 2012-04-09
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-09
Every startup I see this window , but I want to disable it 

[IMG]http://img7.imagebanana.com/img/s21ovw0n/UnlockLoginKeyring_035.png[/IMG]

---

### Post by searchfgold6789 on 2012-04-09
Delete the default keyring by carefully pasting the following code into the terminal:```
cd $HOME
rm ./.gnome2/keyrings/default.keyring
```
I had to do this for my Kubuntu upgrade as well.

---

### Post by dylan07 on 2012-04-09
> **searchfgold6789 said:**
> Delete the default keyring by carefully pasting the following code into the terminal:```
cd $HOME
rm ./.gnome2/keyrings/default.keyring
```I had to do this for my Kubuntu upgrade as well.

this is a good answer.

---

### Post by forsubhi on 2012-04-10
I get this error 

```
subhi@subhi-pc:~$ rm ./.gnome2/keyrings/default.keyring
rm: cannot remove `./.gnome2/keyrings/default.keyring': No such file or directory
```

I use kubuntu 11.10

---

### Post by SeijiSensei on 2012-04-10
Try just

```
cd ~; rm .gnome2/keyrings/default.keyring
```

If that doesn't work, do you see a $HOME/.gnome2 directory if you run "ls -a ~"?  If so, try "ls -laR ~/.gnome2"?  Is there a keyrings directory?

---

### Post by forsubhi on 2012-04-11
this is the output 

```
subhi@subhi-pc:~$ ls -laR ~/.gnome2/keyrings
/home/subhi/.gnome2/keyrings:
total 16
drwx------ 2 subhi subhi 4096 2012-04-11 17:07 .
drwx------ 5 subhi subhi 4096 2012-04-10 00:03 ..
-rw------- 1 subhi subhi 2097 2012-04-11 17:07 login.keyring
-rw------- 1 subhi subhi  207 2011-11-06 03:56 user.keystore

```

---

