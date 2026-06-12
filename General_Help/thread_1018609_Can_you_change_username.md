---
title: "Can you change username?"
date: 2008-12-22
forum: General Help
---

### Post by Yorkie125 on 2008-12-22
I've set up a Ubuntu machine including various updates, software etc, and I have cloned it for someone else (using Clonezilla) so I have an identical copy on another PC. The only problem is that I named my user account with my name. Is it possible to change the username to their name?

In Users and Groups, 'Username' is greyed out so I can't change it. I've tried searching for a solution but can't find anything. Creating a new account causes some software to not work as it's installed to the original account.

Any advice would be greatly appreciated!

Thanks in advance. c :)

---

### Post by eBoxNet on 2008-12-22
Check this..will help you "rename" your user and keep your progs running.

[http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

---

### Post by unutbu on 2008-12-22
If the cloned account's home directory is empty, then this should work okay. If you use wine, or have made a lot of gnome configurations, then changing your username can become a hellish experience. The problem is that many configuration files save absolute path names like /home/Yorkie125/blah/blah in the contents of the configuration file. You would have to change every occurrence of Yorkie125 in every configuration file to make the new account work properly.

Wine is also a problem because it creates symlinks with the old username built into the symlink path. All those symlinks would be broken when you change username. Ugh!

---

### Post by Achetar on 2008-12-22
You can change the username but not the home directory.

This works on gentoo and it should work in ubuntu:
```

$ sudo usermod -l <new-username> <old-username>

```

Then logout and then log back in using the NEW username. That changes the username without changing the $HOME location.

---

### Post by cdtech on 2008-12-22
That command will work but you have to change the "home" directory using the "sudo mv ./oldusername ./newusername" and then change the owner using "sudo chown -R newuser ./newusername"

**UPDATE::.**
Forgot to mention that you will have to change the "newusers" home directory location within the "/etc/passwd" file.

---

### Post by Achetar on 2008-12-22
@cdtech: Moving the home directory and chmodding it appropriately can be accomplished with the following:
```

$ sudo usermod -md /path/to/new/home <username>

```

It is a VERY BAD IDEA to manually edit the passwd file. If you make a typo that system is screwed.

man usermod to find out how you can change users in every possible way.

---

### Post by jerome1232 on 2008-12-22
To avoid all that couldn't you also create a symlink to your new home that has the same name as the old user's home directory?

This way anything pointing to /home/olduser will still end-up in the right spot.

---

### Post by Achetar on 2008-12-22
yes, or you could just not move the home directory in the first place (per my first post). Not all programs will follow symlinks properly.

---

### Post by Yorkie125 on 2008-12-23
Thanks for all the advice :) However I did come across problems with the home directory and decided to just do a new clean install.

---

