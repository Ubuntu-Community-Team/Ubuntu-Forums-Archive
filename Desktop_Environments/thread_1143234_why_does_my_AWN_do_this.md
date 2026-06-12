---
title: "why does my AWN do this?"
date: 2009-04-29
forum: Desktop Environments
---

### Post by timstone on 2009-04-29
Every time I boot my AWN does this, and I have to close it and reopen to get it to fix...

Anyone know why this might be happening?

[IMG]http://img228.imageshack.us/img228/8270/screenshotbvl.png[/IMG]

i know its hard to see but basically when the icons scroll onto the screen its just that big gray box and they never appear

---

### Post by wsonar on 2009-04-29
Has it ever worked correctly? 

Does Compiz work correctly?

Do you have the restricted drivers for your video card enabled?

---

### Post by timstone on 2009-04-29
> **wsonar said:**
> Has it ever worked correctly? 

Does Compiz work correctly?

Do you have the restricted drivers for your video card enabled?


yes the restricted drivers are enabled and it worked fine until i installed Jaunty

---

### Post by wsonar on 2009-04-29
Hmmm 

you may want to kill it then launch it from a terminal window this may give more information as to why it is hanging.

---

### Post by timstone on 2009-04-29
funny....when trying to run it from a terminal it says its not even installed...but i can close the one that messes up and open it up...lol....ill just try to reinstall and see what that does

edit: got this when doing sudo apt-get avant-window-navigator

```

Processing triggers for python-support ...
/var/lib/python-support/python2.6/sqlalchemy/ext/activemapper.py:262: SyntaxWarning: assertion is always true, perhaps remove parentheses?
  assert(version_id_col_object is not None, "version_id_col (%s) does not exist." % version_id_col)

```

---

### Post by wsonar on 2009-04-29
> **timstone said:**
> funny....when trying to run it from a terminal it says its not even installed...but i can close the one that messes up and open it up...lol....ill just try to reinstall and see what that does

edit: got this when doing **sudo apt-get avant-window-navigator**

```

Processing triggers for python-support ...
/var/lib/python-support/python2.6/sqlalchemy/ext/activemapper.py:262: SyntaxWarning: assertion is always true, perhaps remove parentheses?
  assert(version_id_col_object is not None, "version_id_col (%s) does not exist." % version_id_col)

```

what paramater did you give apt-get?

you may want to try 


sudo apt-get remove avant-window-navigator
then
sudo apt-get install avant-window-navigator

---

