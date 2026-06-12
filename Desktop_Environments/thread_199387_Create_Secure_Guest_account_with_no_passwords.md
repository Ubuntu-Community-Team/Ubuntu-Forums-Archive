---
title: "Create Secure Guest account with no passwords"
date: 2006-06-18
forum: Desktop Environments
---

### Post by beowulf62381 on 2006-06-18
I realize that no password and secure are opposing thoughts, but if at all possible i would like to blend the two.

What i would like is a “Guest” account on my notebook that

1.Needs no password to log into.
2.can network manager with no password for keyring
3.is not asked for a password when screen blanks or screen saver comes on
4.No need for any other passwords that would come up for a very limited user account

on the security side I don't want this account to be able to do anything system wide or any thing out side of ~/ I'm still new to Linux so I would like some suggestions on how to lock this account down like no su privileges for this user and so forth.

I hope this post does not come over as to needy but search/read/ask/repeat seems to be the best/only way I learn things.

thank you

---

### Post by beowulf62381 on 2006-06-18
I have have the Guest account setup so no pass word is needed from gdm

using the “auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user” method

can i do something similar  with for network manager and screen saver/blank screen?

---

### Post by mlind on 2006-06-18
[QUOTE=beowulf62381]I realize that no password and secure are opposing thoughts, but if at all possible i would like to blend the two.

What i would like is a &#8220;Guest&#8221; account on my notebook that

1.Needs no password to log into.
2.can network manager with no password for keyring
3.is not asked for a password when screen blanks or screen saver comes on
4.No need for any other passwords that would come up for a very limited user account

on the security side I don't want this account to be able to do anything system wide or any thing out side of ~/ I'm still new to Linux so I would like some suggestions on how to lock this account down like no su privileges for this user and so forth.

I hope this post does not come over as to needy but search/read/ask/repeat seems to be the best/only way I learn things.

thank you[/QUOTE]

1) for Gnome, this can be done by modifying pam authentication

```

[LIST]
[*]create /etc/gdmnopassusers file and insert put guest accounts username there
[*]add directive 
[code]
auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user

``` to /etc/pam.d/gdm file, before @include common-auth directive
[/LIST]

2) I don't know about this. Could be done by assigning Guest to usergroup with this permission, or by modifying /etc/sudoers and defining rule for network manager

3) I'm not sure what happens to screen locking when you create user without password. This could work automatically. passwd -d *useraccount* will remove
user's password

4) This depens what usergroups you assign the guest user. Reviewing different usergroups and their privileges should help

---

### Post by joelito on 2006-06-19
@mlind:

I just followed your instructions, they worked nicely, thanks

---

