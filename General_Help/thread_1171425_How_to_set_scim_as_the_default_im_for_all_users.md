---
title: "How to set scim as the default im for all users?"
date: 2009-05-27
forum: General Help
---

### Post by csh on 2009-05-27
I run the command "im-switch -z en_US -s scim", but this only apply to only one account.

How to set scim as the default im for all users?

---

### Post by prinny42 on 2009-05-27
I haven't tried this myself, but according to the readme, system-wide settings can be modified by executing im-switch as root.  So all you should need to do to set SCIM as the default IM for all users in the en_US locale is:

```
sudo im-switch -z en_US -s scim
```

---

### Post by csh on 2009-05-27
> **prinny42 said:**
> I haven't tried this myself, but according to the readme, system-wide settings can be modified by executing im-switch as root.  So all you should need to do to set SCIM as the default IM for all users in the en_US locale is:

```
sudo im-switch -z en_US -s scim
```

Thanks for your reply.

But the command bring the following errors in terminal

```
No system wide default defined just for locale en_US .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: Cannot find alternative `/etc/X11/xinit/xinput.d/scim'.
```

Anyways to solve it?

Not only in Xubuntu. I want to do it for Ubuntu on another computer. Can I?

---

### Post by prinny42 on 2009-05-27
It looks like setting a system-wide setting for only a specific locale is impossible.  As long as you don't mind setting SCIM as the default IM for all users in all locales, this will probably work:

```
sudo im-switch -z all_ALL -s scim
```

Also, yes, im-switch is DE-independent as far as I know.

---

### Post by csh on 2009-05-27
> **prinny42 said:**
> It looks like setting a system-wide setting for only a specific locale is impossible.  As long as you don't mind setting SCIM as the default IM for all users in all locales, this will probably work:

```
sudo im-switch -z all_ALL -s scim
```

Also, yes, im-switch is DE-independent as far as I know.

This command produce the error message "update-alternatives: Cannot find alternative `/etc/X11/xinit/xinput.d/scim'.

Nevermind, I had found a solution, that is to add something in the /etc/profile file. I will post a howto: later.

However, I would like to thanks anyone who replied to this thread.

If anyone found any solution by to the above error message without editing the /etc/profile file, kindly please post it here. Thank you and have a nice day.

---

### Post by csh on 2009-05-28
I just realise that there is a Ubuntu help page for setting up scim.

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

---

