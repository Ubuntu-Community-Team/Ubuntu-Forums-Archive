---
title: "Application Menu not working"
date: 2008-02-24
forum: Desktop Environments
---

### Post by hulio40 on 2008-02-24
my applications section in the main menu is gone i dont know how and im a big noob in ubuntu and dont know how to run my applications from else then my applications menu when i put the other kind of menu the application menu is empty and cant add anything to it i didnt delete anything and when i do edit menus it doesnt start pls help :confused:

---

### Post by pytheas22 on 2008-02-24
First of all, if you haven't already, try rebooting and see if the problem is solved.

If that doesn't work, press alt-f1 and you will get an application menu.  From there, open a terminal and enter the command

```
ps -e | grep panel
```

You should see something like
```

5527 ?        00:00:45 gnome-panel
```

Take note of the number to the left (in the above case, 5527, but yours will be different), and enter the command

```
kill 5527
```

to kill the panel.

Then at the command line enter```


gnome-panel
```

and hopefully that will make the panel come back properly.  If it doesn't, post.  Also, for clarification, is it only the Applications menu part of the panel that is missing, or is the whole thing gone (including the system tray containing the Network Manager icon and so on)?

---

### Post by hulio40 on 2008-02-25
dude the whole application ting is gone i do alt+f1 and i get only places and system no applications and yes i rebooted

---

### Post by pytheas22 on 2008-02-25
if you press alt-f2 can you launch applications that way, either by typing their name or selecting them from the list?

---

### Post by nardis_Miles1 on 2008-02-25
I have a related problem. Thoughtlessly, I removed NetworkManager and I have now replaced it. However there is no icon in the system tray. I know NM is running because I see it in ps -ax. Is there a way to add the nm-applet back into the system tray?

---

### Post by hulio40 on 2008-02-25
> **pytheas22 said:**
> if you press alt-f2 can you launch applications that way, either by typing their name or selecting them from the list?

yes i can ive launched some of my programs that i knew the name like that but cant remember all

---

### Post by pytheas22 on 2008-02-25
> yes i can ive launched some of my programs that i knew the name like that but cant remember all

ok, then we know that your programs exist and start properly.

Next thing to try: go to Administration>Users and Groups and create a new user account with the default settings.  Log out of Gnome and log back in with the new user's credentials.  Does the Applications menu appear normally now?  This will tell us whether the problem is with your local user configuration or a more global problem.

---

### Post by pytheas22 on 2008-02-25
> I have a related problem. Thoughtlessly, I removed NetworkManager and I have now replaced it. However there is no icon in the system tray. I know NM is running because I see it in ps -ax. Is there a way to add the nm-applet back into the system tray?

I've had issues exactly like this and have never solved them; NM is notoriously buggy and I suspect that that' s the source of the problem.  You could try searching the forums for a solution or start a new thread.  Another option is to use wicd instead of NM: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by hulio40 on 2008-02-25
yes all applications r there in a new administrator account i just made

---

### Post by pytheas22 on 2008-02-25
try doing this:

```
cd ~/.config/menus/
rm applications.menu
```

I got this from this thread [http://ubuntuforums.org/showthread.php?t=576703](http://ubuntuforums.org/showthread.php?t=576703) :

---

### Post by hulio40 on 2008-02-25
> **pytheas22 said:**
> try doing this:

```
cd ~/.config/menus/
rm applications.menu
```

I got this from this thread [http://ubuntuforums.org/showthread.php?t=576703](http://ubuntuforums.org/showthread.php?t=576703) :



Omg thx alot its back up and i can run edit menus! :guitar:

---

