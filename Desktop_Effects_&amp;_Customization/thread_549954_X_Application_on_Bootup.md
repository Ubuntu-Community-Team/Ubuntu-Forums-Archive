---
title: "X Application on Bootup"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by carstenson on 2007-09-13
I'm not sure if this is the correct forum, but here goes.

I want to start up firefox (or whatever X application) on a virtual terminal whenever I boot. I want it to be persistant, like a kiosk, where it will restart on exit. I don't want to go through authorization. I don't want it to run in a Desktop Environment. Just that application in X.

I thought that gdm would work for me, but didn't have any luck. I got it to start the empty X server, but couldn't come up with a way to get the application to run on that display. I was suprised to learn that X cannot start an application.

I then removed it from gdm and tried out xinit. This works great from a shell prompt. I tried putting this in /etc/event.d, but this didn't work. I get the X server, but no firefox process. The haven't found much in the logs. I think daemon.log shows that it just keeps restarting. It occurred to me that I need to make this a daemon process, where it doesn't block. I'm not sure how to accomplish this.

If anyone has any ideas on this, even a new way to accomplish this, I would appreciate it.

I am very new to Ubuntu. I feel that Linux finally can compete with Windoze for ease of install / ease of use. Great job ________.

---

### Post by chewearn on 2007-09-13
Not sure if these are what you looking for, but here goes:

1. Auto start-up application
Top Panel Menu > System > Preferences > Sessions
The first tab is "Start-up Programs"; just create an item for your application here.

2. No authentication when boot up (a.k.a. auto-login)
Top Panel Menu > System > Administration > Login Window
Under "Security" tab, check "Enable Automatic Login", and select the user.

---

### Post by carstenson on 2007-09-13
Good stuff, Alta, but I don't think it is quite what I'm looking for. Let me explain a little bit more. I'm wanting this firefox process to run on vt12 (tty12). I want the standard login screen to run on vt7. I am setting this up at home and want an extremely quick, easy way of always getting to a browser screen. I don't care about security, nor having a login. I could setup a guest user with auto login, but still have issues.

1. I'd rather not have the Gnome (or any other) desktop running on this auto window. Just the single application

2. If I enable the automatic login, will this apply to the vt7 screen?

Thanks for the reply.

---

### Post by chewearn on 2007-09-13
Ok, I re-read your post and see what you are getting at.  Sorry for not understanding your intent earlier.

From what I can tell, you are trying to set-up a locked down linux box, which can only run firefox for the user.  I don't have the expertize in linux to help much here.  Currently, I'm slogging thru self learning of a barebone linux setup ([http://www.linuxfromscratch.org/);](http://www.linuxfromscratch.org/);) still far from being able to suggest how to make such a setup.

Another possibility here is to work backward, from a basic ubuntu desktop installation, then start to strip down everything.  Create a user with minimal access rights.  Then, uninstall every extra applications, remove the gnome panels, etc.  Since the user can't install anything, can't run sudo, he can't mess with anything outside his home directory.

Sorry, can't give any advice on the vt/tty stuffs.  Absolutely no knowledge there.

---

### Post by pointone on 2007-09-13
Using inittab, you could add a line to respawn a script: for example:

```
...
l2:2:wait:/etc/init.d/rc 2
x2:2:respawn:/path/to/your/script
...
```

Where your script is something along the lines of:

```
su --command="startx" username
```

Then you can edit /home/username/.xinitrc to include:

```
<WINDOW MANAGER> &
exec firefox
```

Without inittab (i.e. Ubuntu > Edgy), you'll need to edit one of the /etc/event.d/tty* files (presumably tty12) to read:

```
...
respawn
exec /sbin/getty /path/to/your/script 38400 tty*
```

Hope this helps.

---

