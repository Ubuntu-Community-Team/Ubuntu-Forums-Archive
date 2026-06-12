---
title: "Cannot access Users and Groups"
date: 2009-03-24
forum: General Help
---

### Post by cupevampe on 2009-03-24
Hi everyone

a few days ago i have created a new admin user and since then i cannot open System > Administration > Users and Groups 

I get a message saying I am not allowed to accedd the configuration.

I tried from my new user, I could open Users and Groups but when trying to unlock it, Ubuntu would hang and then tell me there was an error.

From the new admin I could edit the sudoers list and added my old username (my main user) to it, because i lost the capability of sudoing. Now i can sudo again.

Any idea how to fix this? Many thx!

---

### Post by milan.satala on 2009-03-24
I get the same error. However I've never had any problems with sudo. 
Try to run users-admin from terminal and post your output here.
I tried to unlock Users Settings and got following error:
```
** (users-admin:7230): CRITICAL **: Message did not receive a reply (timeout by message bus)
```
Another affected application is ubuntu-tweak which printed a longer error message into terminal:
```
ERROR:dbus.proxies:Introspect error on :1.2586:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

---

### Post by cupevampe on 2009-03-24
This is what i get

```
invalid string constant "#E4E4E4", expected valid string constant

(users-admin:7611): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

```

is it a gtk issue?

it still says configuration cannot be loaded!

---

### Post by cupevampe on 2009-03-25
Apparently i got this solved although its not easy to say how

fisrt of all i logged on as graphical root (google it to know how to) and deleted the account i created a few days ago, because since its creation ive had problems
its name was admin and i've deleted it 

then i checked all the Advanced options in Users and Groups for my user

finally i modified visudo to include username ALL=(ALL) ALL just below root All=(ALL) ALL

then i relogged in with my old username and now everything seems in order

sorry the explanation is not very tech
:guitar:

---

