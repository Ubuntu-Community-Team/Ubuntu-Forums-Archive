---
title: "Problem with adding user to group"
date: 2009-02-26
forum: General Help
---

### Post by ThaddeusW on 2009-02-26
Hello everyone,

I am busy working with the Valve Source dedicated server (srcds). My idea is to move the whole srcds install to the /srv directory and then let it be owned by root and the group srcds. I am creating a user called tf2 that will run the server but I am trying to add the user to the srcds group but I cant add the tf2 user to the group. Yes the group was created by groupadd and the group exists. 

This is the output get from "#useradd -G srcds tf2"
```
useradd: user tf2 exists
```
How can the user exist when he does not? "id tf2" does not show tf2 belonging to any other gropu other then its own.

---

### Post by Kumpe on 2009-02-26
Long time since i used this, but i'm pretty sure you don't need any options when adding an already existing user to a group. Have you tried it without the "-G"? 
Otherwise i would edit "/etc/group" and add the user manually.

---

### Post by sisco311 on 2009-02-26
> **ThaddeusW said:**
> Hello everyone,

I am busy working with the Valve Source dedicated server (srcds). My idea is to move the whole srcds install to the /srv directory and then let it be owned by root and the group srcds. I am creating a user called tf2 that will run the server but I am trying to add the user to the srcds group but I cant add the tf2 user to the group. Yes the group was created by groupadd and the group exists. 

This is the output get from "#useradd -G srcds tf2"
```
useradd: user tf2 exists
```
How can the user exist when he does not? "id tf2" does not show tf2 belonging to any other gropu other then its own.

it's:
```
usermod -aG group username
```
or
```
adduser username group
```


or #*gpasswd -a username group*

---

### Post by jerremy-tamlin on 2009-02-26
I have a similar problem.

Apologies if its not related but I think it is.

I want to make myself a member of group root so I can set the root files I want to be able to edit to 775 and not have the danger of getting very used to typing sudo all the time which basically renders it's advantages over su root negligible.

I have added myself to group root and when I do:
```
$ sudo adduser jerremy root
The user `jerremy' is already a member of `root'.

```

But then if I do
```
$ groups
jerremy adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin opt

```
group root isn't there and I get access denied messages when I try to modify files like this:
```
-rwxrwxr-x 1 root root 1681 2008-08-30 13:57 robots.txt

```

Sorry if this is a different issue but I thought there might be something similar going on.

Oh also have you looked in /etc/group ? I believe this is the underlying file that holds group information.
It's format is like this:
```
group_name:passwd:GID:user_list
root:x:0:jerremy
...
jerremy:x:1000:
ntop:x:120:
etc.
```

---

### Post by Yellow Pasque on 2009-02-26
> **jerremy-tamlin said:**
> I want to make myself a member of group root so I can set the root files I want to be able to edit to 775 and not have the danger of getting very used to typing sudo all the time which basically renders it's advantages over su root negligible.

That's not the point of 'sudo', and giving your user root group permissions would be a fundamentally bad idea security-wise.

Also, IIRC, only the root user can be in the root group anyway.

---

