---
title: "GUI to change password"
date: 2005-05-02
forum: Desktop Environments
---

### Post by chip33az on 2005-05-02
I set up an Ubuntu workstation in an office for a friend and didn't hand out the root password or account.  I set up the users to log in, but now a few of them want to be able to change it.

Is there a tool to do that besides the command line passwd?  They can't get into Users/Groups since they aren't the root.

Any info would be helpful.

---

### Post by bored2k on 2005-05-02
1) [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)
2) users-admin

---

### Post by chip33az on 2005-05-03
So I would have to grant the person who wants to change their password administrator access, if I am reading the link correctly.

That would give them a little more power than I really want.

---

### Post by shakin on 2005-05-03
You raise a very good point. Unless I am missing something, there is no GUI password changer. I've never looked, but I'm also not aware of a generic one that can be installed, only distro-specific ones. I'm sure one of those could be ripped out of another distro and put into Ubuntu.

As a workaround you can create a shell script like this:
```

#!/bin/bash
passwd
exit;

```
Make it executable and add it to the menu with a nice icon. It will popup the command line password change app, which is easy enough for anybody to use.

---

### Post by Stormy Eyes on 2005-05-03
[QUOTE=shakin]Make it executable and add it to the menu with a nice icon. It will popup the command line password change app, which is easy enough for anybody to use.[/QUOTE]

When creating the menu item, make sure to click on the "run in terminal" option.

---

### Post by Alexander Kirillov on 2005-05-03
[QUOTE=shakin]You raise a very good point. Unless I am missing something, there is no GUI password changer. I've never looked, but I'm also not aware of a generic one that can be installed, only distro-specific ones. I'm sure one of those could be ripped out of another distro and put into Ubuntu.
[/QUOTE]
In particular, RedHat/Fedora has such a GUI tool, called userpasswd. Maybe we should suggest to Ubuntu developers that this tool be included (with necessary changes) to Ubuntu?

---

### Post by wolovids on 2005-05-03
[QUOTE=Alexander Kirillov]In particular, RedHat/Fedora has such a GUI tool, called userpasswd. Maybe we should suggest to Ubuntu developers that this tool be included (with necessary changes) to Ubuntu?[/QUOTE]I agree that this type of app (although very simple) is a necessity.  New users should not have drop down to a prompt at all.  I couldn't imagine telling my wife to open a terminal window!

Edit: Here's the Ubuntu [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=8090) and here's the Gnome upstream [bug](http://bugzilla.gnome.org/show_bug.cgi?id=71215)

---

