---
title: "Changing the ugly login screen?"
date: 2010-09-19
forum: Desktop Environments
---

### Post by CaptSaltyJack on 2010-09-19
I really hate 10.04's login screen. Ugh. And I don't like that it lists all the users on the box. What happened to those clean-looking login screens, that just prompt you to type a username? Can I change the login screen appearance, somehow? I seem to recall that was possible, though I can't find anything in the preferences.

---

### Post by Chris1274 on 2010-09-19
> **CaptSaltyJack said:**
> I really hate 10.04's login screen. Ugh. And I don't like that it lists all the users on the box. What happened to those clean-looking login screens, that just prompt you to type a username? Can I change the login screen appearance, somehow? I seem to recall that was possible, though I can't find anything in the preferences.
 
I believe that option was taken away with Lucid in the cause of faster boot-ups. You can change the login background, but not the box itself.

---

### Post by CharlesA on 2010-09-19
Check the post [here]("http://ubuntuforums.org/showpost.php?p=9487803&postcount=5").

---

### Post by CaptSaltyJack on 2010-09-19
Grumble. Why'd they get rid of the option to change the layout of the login screen and hide the user list?? I wish they'd get some people on their team with some design sense. The 10.04 login screen is uuuugly.

---

### Post by panel123 on 2010-09-19
it's simple if you hate the login screen then change it.. change into the screen want you want it easy  hehe :D

 but you can't change the list of all users in the box..
only the background...

---

### Post by sisco311 on 2010-09-19
> **CaptSaltyJack said:**
> I really hate 10.04's login screen. Ugh. And I don't like that it lists all the users on the box. What happened to those clean-looking login screens, that just prompt you to type a username? Can I change the login screen appearance, somehow? I seem to recall that was possible, though I can't find anything in the preferences.

To disable the user list, run:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list "true"
```

To (re-)enable the user list, run:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list "false"
```

If you want to change the theme, wallpaper...,then add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

If you want to change the look of the simple greeter, then learn how to use GLADE and create new theme(s) for the new GDM. :evil:

---

### Post by CaptSaltyJack on 2010-09-19
It's more than just the background I don't like. It's the layout of the box itself.. etc. It just looks ugly.

HERE is a sexy login screen:
[http://www.ahlera.com/blog/wp-content/uploads/2008/11/08.jpg](http://www.ahlera.com/blog/wp-content/uploads/2008/11/08.jpg)

---

