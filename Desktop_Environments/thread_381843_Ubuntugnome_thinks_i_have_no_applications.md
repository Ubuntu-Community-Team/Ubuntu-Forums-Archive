---
title: "Ubuntu/gnome thinks i have no applications"
date: 2007-03-11
forum: Desktop Environments
---

### Post by Parag2k3 on 2007-03-11
I'm not exactly sure how this happened, but now the application menu doesn't work. When i right click on the menu and try to edit it, the menu layout window opens and then quickly closes. 

The places and system menus still work fine. I also have no access to the terminal. When I try to add an application launcher to the panel, it doesn't see any programs besides for the ones in the system menu.

What am I supposed to do??

---

### Post by kvonb on 2007-03-11
I can offer a quick and dirty method :)

What I propose doing is creating a new login, it's unlikely that any essential system files have been affected unless you logged in as root!

So I would suggest forgetting the current user's desktop and make a new one, you can copy any important files over later.

Press <ALT><F2> and hopefully the run dialogue will come up, if it does, type in:

```
gksu users-admin
```

That should load the Users control.

Add a new user, and make sure you select "allow to administer the system" on the 2nd tab.

Save and close, then in the run box, type:

```
gksu gdmsetup
```


Now on the security tab (I think), select the new user to be automatically logged in, save and exit.

Now simply press <CTRL><ALT><BACKSPACE> and it should automatically log you back in as the new user.

If it still has lost menus, then I'm afraid I can't help :).

Regards, KEv :)

---

### Post by Parag2k3 on 2007-03-11
that worked perfectly
thank you so much

---

### Post by kvonb on 2007-03-11
Excellent :)

Now if you want your original username back, do the same thing, but use your old username.

It should work :)

---

