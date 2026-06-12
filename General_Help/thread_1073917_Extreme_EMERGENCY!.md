---
title: "Extreme EMERGENCY!"
date: 2009-02-18
forum: General Help
---

### Post by blackrockzig on 2009-02-18
I need help. FAST! I was uninstalling cairo and I guess I hit the wrong thing because everything just went away! I can't get back to admin. All the icons disappeared. I can't open any files. Can any one help? I am using another computer because I can't use mine!


I noticed my music programs are gone. Most things are just gone. I hope there is a back log on what newb mistake I just made.

Thank you in advance

---

### Post by dasunst3r on 2009-02-18
If you are able to get into the terminal and have Internet access, reinstall the package *ubuntu-desktop* by issuing the command *sudo apt-get install ubuntu-desktop*.

---

### Post by blackrockzig on 2009-02-18
could not launch menu item.
'failed to execute child process "gnome-terminal"(No such file or directory)

---

### Post by Therion on 2009-02-18
Try using Ctrl+Alt+F2 to drop to a shell.

Then try using ```
sudo apt-get install ubuntu-desktop
```

Then type in "reboot" to restart your system, or use Ctrl+Alt+F7 to return to the desktop.  

You may need to restart X, though, I'm not sure...

---

### Post by cariboo on 2009-02-18
Who's going to die if this doesn't get fixed? Use a better title for your post.

Jim

---

### Post by blackrockzig on 2009-02-18
> **Therion said:**
> Try using Ctrl+Alt+F2 to drop to a shell.

Then try using ```
sudo apt-get install ubuntu-desktop
```

Then type in "reboot" to restart your system, or use Ctrl+Alt+F7 to return to the desktop.  

You may need to restart X, though, I'm not sure...


working so far

---

### Post by heindsight on 2009-02-18
Try pressing Ctrl+Alt+F1, enter your username and password to log in,
then do 
```
sudo apt-get install ubuntu-desktop
```

If that works, you may have to do
```
sudo invoke-rc.d gdm restart
```

and then press Ctrl+Alt+F7 (or maybe F9) to get back to your gnome login screen. 

You'll probably also have to reinstall all packages that depend on ubuntu-desktop

---

### Post by blackrockzig on 2009-02-18
> **cariboo907 said:**
> Who's going to die if this doesn't get fixed? Use a better title for your post.

Jim

Thanks for nothing.

BTW all my information is on this laptop Sir!

---

### Post by Therion on 2009-02-18
> **blackrockzig said:**
> It asks for Zach-laptop login.
Then it asks for login
Then is says login incorrect
I know what the password is, but I never had to type anything for a login. any ideas?
It wants your usual user-name and password...  

I don't know what those are, obviously, but I'm going to guess your user name might be "zach".  You were required to provide a user-name and password when you installed Ubuntu.  That's what it's asking for.

Ah, just saw your edit... So you're rocking and rolling so far.  Good.  Once you're back up and running it might be a good time to make some backups.

---

### Post by blackrockzig on 2009-02-18
> **Therion said:**
> It wants your usual user-name and password...  

I don't know what those are, obviously, but I'm going to guess your user name might be "zach".  You were required to provide a user-name and password when you installed Ubuntu.  That's what it's asking for.

Ah, just saw your edit... So you're rocking and rolling so far.  Good.  Once you're back up and running it might be a good time to make some backups.

How so...

It's installing as we speak.

---

### Post by blackrockzig on 2009-02-18
Thank you guys so much!!!

I am using my laptop as we speak!

I wrote everything down that you guys said so I know what to do if this ever happens again.

Now the problem is figuring out what personalisation I had on before. Like how to fix the media bug I have or actually be able to use cairo dock and such. 

I do thank you all!

---

### Post by blackrockzig on 2009-02-18
An error occurred while loading or saving configuration information for gnome-appearance-properties. Some of your configuration settings may not work properly.

Do you know what this means??

---

