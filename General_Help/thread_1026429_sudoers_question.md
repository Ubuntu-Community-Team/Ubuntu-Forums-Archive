---
title: "sudoers question"
date: 2008-12-31
forum: General Help
---

### Post by bigman1052 on 2008-12-31
This is just a quick question that has been on my mind since I setup ubuntu server a few days ago.  When I setup the server and I created the default user I used my name "wes".  Of course we all know that this account is an administrator with sudoer privileges.  Now when when I use visudo or nano to edit /etc/sudoers its not in there.  Like i said this is just one of those questions that has been on my mind since I started using linux about a week ago.

---

### Post by theinnercityhippy on 2008-12-31
try typing

:>id wes

This will most likely tell you that you belong to the admin group, and it is this group that is listed in the /etc/sudoers file.

Hope this de-boggles you a little :-)

-JimDog*-

---

### Post by theinnercityhippy on 2008-12-31
> **theinnercityhippy said:**
> try typing

:>id wes

This will most likely tell you that you belong to the admin group, and it is this group that is listed in the /etc/sudoers file.

Hope this de-boggles you a little :-)

-JimDog*-

Sorry that was a little confusing, the command is

id wes

the bit before was meant to look like the command prompt lol

---

### Post by namdung on 2008-12-31
In terminal
```
id
```

If u see *admin* in the list the u r part of the admin group.

Now in sudoers file
```
sudo cat /etc/sudoers
```

U'll find:
> 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Which means admin group has root privileges and since u r part of the admin group u'll have root privileges too.

---

### Post by bigman1052 on 2008-12-31
Cool, I figured thats what it was.  Just didnt see my actual ID anywhere.  Been using linux for about a week, got the server setup, forwarded port22 for my SSH, got the web server setup, setup the network for a static IP, forwarded the rest of the ports for webmin and http, aswell as a subversion repo.  HEY! got myself a webserver.  thanks for the help guys, just one of those things in the back of your head.

---

### Post by glotz on 2008-12-31
Welcome to the penguin side of things then stranger! And remember, when in doubt, *<snip>*;```
man sudoers
```

---

