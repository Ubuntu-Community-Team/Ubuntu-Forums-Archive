---
title: "Screen Freeze/Darken after any gksu or gksudo use"
date: 2007-04-12
forum: Desktop Environments
---

### Post by StoneUSA7 on 2007-04-12
I've had Fiesty installed on my laptop for a few weeks now, and everything has been fine.  Recently though, anytime I go into the System>Administration> menu and choose an application, it will ask me for an Admin password, I'll enter it, then the screen will go dark, like when it asks for the password, but nothing else happens.  There will be minimized window in the bottom panel that says "Starting Administrative Application" and I can move the mouse, but I can't interact with the desktop or anything else.  I end up having to hard reset the computer to bring it back to life.  I tried typing an incorrect password and it did the same.  

So, I came to the forums and did a bit of searching and tried to run it from the Terminal with gksu and gksudo.  Same problem.  But if I use just sudo  or su then it runs fine without freezing.  When I run it from the Terminal with gksudo, I get no error messages, just a frozen screen, yet the mouse still works.

I tried running sudo apt-get update/upgrade to see if that would fix the problem, but it's still the same.

I'm not sure if this is related, but since this has been happening, when Nautilus starts up, there are usually 3 icons on the splash screen, but now there are only 2?  Maybe this has nothing to do with it.

It's not a massive problem, but it sucks that I have to go to the Terminal every time I want to run an administrative application.  Anyone have any ideas what's going on, or where I should look to fix this?

Thanks!

---

### Post by aysiu on 2007-04-12
Well, first of all, don't use *sudo* with any graphical applications. I know that seems to be the only thing that's working right now, but it may also be contributing to things being broken... or break something else in the near future.

Can you try creating a new test user (you can always delete this user later) and seeing if that test user runs into the same problem? ```
sudo adduser testuser
sudo adduser testuser admin
exit
``` Then log in as the test user and try to run an administrative application like System > Administration > Login Window

If it works for the test user, something's wrong with your user config. If you get the same problem, you have a system-wide configuration issue.

---

### Post by StoneUSA7 on 2007-04-12
Well you hit it right on the head.  The testuser account worked fine.  Is there a way to reset/fix my user config, or should I just same my /home folder and make a new account?

---

### Post by aysiu on 2007-04-12
Here's one thing you can try. It's possible that through using *sudo* for graphical apps instead of *gksudo*, you might have accidentally changed ownership to root of some of your home configuration files.

If your regular username is *stone* (use your actual username, of course), type this command into the terminal: ```
sudo chown -R stone:stone /home/stone
``` This will change ownership of all the files in your home directory to the user. Log out and log back in again. See if that made things better. If not, you may just want to make a new account and move over the important files from your old user's home folder.

---

### Post by StoneUSA7 on 2007-04-12
Well unfortunately changing the ownership of the directory didn't work.  But that's okay, it's not very hard to copy over the important files.  I'm glad that I did learn one important rule, that I shouldn't be running any graphical apps with sudo or su.  Hopefully that will keep me out of trouble next time!

Thanks again for all the help aysiu, I really appreciate it!

---

### Post by aysiu on 2007-04-12
More on that here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You may need to use ```
gksudo nautilus
``` to move the files from /home/originaluser to /home/newuser, and you'll want to do a ```
sudo chown -R newuser:newuser /home/newuser
``` once all your files (pictures, music, videos) have been copied over to make sure the new user owns those files.

Still don't know what caused the problem, but I'm glad that workaround at least works!

---

### Post by Crosbie on 2007-04-21
Here's another, simpler, fix/workaround:

I had the same problem; and I've always disliked the clash there seems to be between xgl desktop effects and the greying-out Gnome (?) seems to want to do when starting admin apps.  (Feels clunky and looks blocky, even when it's not locking the system up :) )

Under System>Preferences>Accessibility>Assitive Technology Preferences you can tick 'Password dialogues as floating windows'.  This gives you a standard window in which to type your password, no greying-out effect, and no lockup for me. Thumbs up all round.

---

