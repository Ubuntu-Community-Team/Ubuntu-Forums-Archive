---
title: "Lock screen replace to gnome-screensaver"
date: 2012-12-20
forum: Desktop Environments
---

### Post by Diamond2 on 2012-12-20
Hello everyone,

Is there any lock screen program can be used with gnome, support PAM?

I am writing a script to display chromium-browser as a screensaver with dbus-monitor to monitor the idle status of gnome, if it's idle, chromium will display a specify web page in kiosk mode.
Then if computer is out of idle mode, chromium-browser will be closed automatically.

The thing I want is when computer is out of idle mode: a dialog box will ask user/password (like gnome-screensaver lock screen). If credential is correct, let user to their desktop after automatically close chromium. If it is not correct, close dialog, continue display chromium-browser. We can't use gnome-screensaver here, because when gnome-screensaver is running, it will be foreground of chromium-browser even the password correct or not.

Searching on internet, I found that xtrlock is something fit my need. Unfortunately, it doesn't support PAM in my environment.

Another thing, is there any shell command to blank out secondary monitor?

Thanks,

---

### Post by sudodus on 2012-12-20
I use an alias to xscreensaver to lock my screen in systems, where there is no obvious default 'lock utility'.

```
alias lock='xscreensaver-command -lock'
```

Maybe you can call xscreensaver-command from your script.

---

### Post by Diamond2 on 2012-12-20
> **sudodus said:**
> I use an alias to xscreensaver to lock my screen in systems, where there is no obvious default 'lock utility'.

```
alias lock='xscreensaver-command -lock'
```

Maybe you can call xscreensaver-command from your script.

I think xscreensaver is same as gnome-screensaver in my case.
If I call xcreensaver-command -lock, it will run in foreground of my screen, then I can't see chromium-browser anymore...

---

### Post by zombifier25 on 2012-12-21
> **Diamond2 said:**
> I think xscreensaver is same as gnome-screensaver in my case.
If I call xcreensaver-command -lock, it will run in foreground of my screen, then I can't see chromium-browser anymore...

You'll need to write a screensaver that runs a specific command for xscreensaver. Shouldn't be too hard, [like this tutorial for running Conky as a screensaver](http://crunchbang.org/forums/viewtopic.php?id=4093).

---

### Post by Diamond2 on 2012-12-23
> **zombifier25 said:**
> You'll need to write a screensaver that runs a specific command for xscreensaver. Shouldn't be too hard, [like this tutorial for running Conky as a screensaver](http://crunchbang.org/forums/viewtopic.php?id=4093).

Thanks, I will try it :)

---

### Post by stinkeye on 2012-12-23
There is a program in the repos called xtrlock which just overlays the screen with a lock icon.
There is no unlock dialogue box. You just type in your password and press enter.

From man xtrlock...
> xtrlock locks the X server till the user enters their password at the keyboard. 

 While xtrlock is running, the mouse and keyboard are grabbed and the mouse cursor becomes a padlock. Output displayed by X programs, and windows put up by new X clients, continue to be visible, and any new output is displayed normally. 

 The mouse and keyboard are returned when the user types their password, followed by Enter or Newline. If an incorrect password is entered the bell is sounded. Pressing Backspace or Delete erases one character of a password partially typed; pressing Escape or Clear clears anything that has been entered. 

 If too many attempts are made in too short a time further keystrokes generate bells and are otherwise ignored until a timeout has expired. 

 The X server screen saver continues to operate normally; if it comes into operation the display may be restored by the usual means of touching a key (Shift, for example) or the mouse.

You may want to also take a look at **xautolock** with xtrlock.
eg this will lock the screen and start firefox after 5 mins idle. Shows a notification 10 secs before locking.
```
xautolock  -notify 10 -notifier 'notify-send "Screen will lock in 10 seconds"' -time 5 -locker "xtrlock & firefox"
```
See **man xautolock**

---

### Post by Diamond2 on 2013-01-04
> **stinkeye said:**
> There is a program in the repos called xtrlock which just overlays the screen with a lock icon.
There is no unlock dialogue box. You just type in your password and press enter.

From man xtrlock...


You may want to also take a look at **xautolock** with xtrlock.
eg this will lock the screen and start firefox after 5 mins idle. Shows a notification 10 secs before locking.
```
xautolock  -notify 10 -notifier 'notify-send "Screen will lock in 10 seconds"' -time 5 -locker "xtrlock & firefox"
```
See **man xautolock**

Thanks for your information. The thing is I can't find xtrlock for ubuntu which is supported PAM...

---

### Post by Diamond2 on 2013-01-07
> **zombifier25 said:**
> You'll need to write a screensaver that runs a specific command for xscreensaver. Shouldn't be too hard, [like this tutorial for running Conky as a screensaver](http://crunchbang.org/forums/viewtopic.php?id=4093).

Hi,

I try added a new entry on my .xscreensaver file
```
GL: chromium-browser --kiosk my_web_URL_here \n\
```

Everytime I open xscreensaver preference, click on "Chromium-browser" screensaver name, it displays chromium-browser but when clicking "Preview", it just displays a blank screen (black color background) with yellow warning message about ssl certificate on the top (the warning may come from chromium because my_web_URL_here is a https link)


BTW, I tried to test with alock (alock-svn-94.tar.bz2), it just only works if you supply the password correctly at first time (I use PAM authentication). If the first time you enter wrong password (output is: pam error:Authentication failure), later you can't unlock even you type correct password (pam error:Success)

Any other suggestions please?

---

### Post by stinkeye on 2013-01-08
Just out of interest what is pam authentication and why do you use it?

---

### Post by Diamond2 on 2013-01-22
> **stinkeye said:**
> Just out of interest what is pam authentication and why do you use it?

[http://code.google.com/p/alock/issues/detail?id=27](http://code.google.com/p/alock/issues/detail?id=27)

Asked on alock :p

---

