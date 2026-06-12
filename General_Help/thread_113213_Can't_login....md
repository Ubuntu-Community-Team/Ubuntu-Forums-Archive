---
title: "Can't login..."
date: 2006-01-05
forum: General Help
---

### Post by ymmotrojam on 2006-01-05
Well, I've been toying around with my system, and I'm a newbie... which has to mean trouble right ;). I was attempting to install PHP5, MySQL, phpMyAdmin and other web server related things. Everything seemed to work fine, until I rebooted. I have no clue what I did or what the error message means, so maybe you guys can help me out...

1. When I attempt to login, I am now greeted with a message that says basically that the session lasted for less than 10 seconds, blah blah...
2. I click for more info and I get the following (this is not all of it, it's only a summary. if you need the whole thing, just let me know)

(gnome-session:7751): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
...
(gnome-session:7751): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
...
(gnome-session:7751): WARNING **: Unable to read ICE authority file: /home/(user)/.ICEauthority

---

### Post by adwait on 2006-01-06
Well, judging from the errors, you could fix things by reinstalling libgail-gnome and libatk-bridge. To do this, at the login screen press Shift + Alt + F1. This will bring you to a console, now login with your username and password. Then use
```
sudo apt-get install libgail-gnome-common
sudo apt-get install libatk1.0-data
sudo apt-get install libatak1.0-0

```

That should take care of the first two errors.

For the last error, try changing the permissions of the .ICEauthority file with
```
chmod +rw .ICEauthority
```

---

### Post by ymmotrojam on 2006-01-06
[quote=adwait]Well, judging from the errors, you could fix things by reinstalling libgail-gnome and libatk-bridge. To do this, at the login screen press Shift + Alt + F1. This will bring you to a console, now login with your username and password. Then use
```
sudo apt-get install libgail-gnome-common
sudo apt-get install libatk1.0-data
sudo apt-get install libatak1.0-0

``` 
That should take care of the first two errors.

For the last error, try changing the permissions of the .ICEauthority file with
```
chmod +rw .ICEauthority
```[/quote]
I just changed the last bit about the .ICEauthority file and it appears to be working again. Thanks for the assistance! :)

---

