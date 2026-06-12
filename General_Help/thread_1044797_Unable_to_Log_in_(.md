---
title: "Unable to Log in :("
date: 2009-01-19
forum: General Help
---

### Post by billytalent on 2009-01-19
Hey guys, 

i installed a login window and now when i boot into my ubuntu it wont let me log in, all i get is the black screen and the mouse turning around. 

What can i do? Need your help bad...

---

### Post by yeats on 2009-01-19
You can drop to a login shell by typing Ctrl-Alt-F1.  From there you can navigate to the logs to see what might be happening or use apt-get to remove (add the --purge flag to remove configuration as well) the login manager.

Hope that helps and good luck.

---

### Post by billytalent on 2009-01-19
> **chrissharp123 said:**
> You can drop to a login shell by typing Ctrl-Alt-F1.  From there you can navigate to the logs to see what might be happening or use apt-get to remove (add the --purge flag to remove configuration as well) the login manager.

Hope that helps and good luck.

Sorry mate, ubuntu is a new experience to me but i know a little, 

so i boot into ubuntu and hit Ctrl-Alt-F1? Once i do that and check the logs where do i go from there...can you gimme a step by step please mate :)

---

### Post by yeats on 2009-01-19
> so i boot into ubuntu and hit Ctrl-Alt-F1? Once i do that and check the logs where do i go from there...can you gimme a step by step please mate 

Yes - when you reach the point where the login manager is stalling, type Ctrl-Alt-F1

you can then login with your normal username and password and you'll see a command prompt.  If you know the name of the login manager package (I'm assuming you got this from the Ubuntu repositories?) you can remove it by typing

```
sudo apt-get remove --purge *package-name*
```

if you want to look in the logs to see what's there, do:

```
cd /var/log/
grep gdm * [this searches all the major logs for "gdm" the gnome display manager]

```

if you post what you find, I or someone else may be able to help you troubleshoot.

You can return to the graphical interface at any time by typing Alt-F7

How did you install the login manager?

---

### Post by billytalent on 2009-01-19
I DL the tar.gz file from gnome and installed it via the login window in admin like always, then there was a tick box for disabling the menu..something...

since then i havent been able to get in...

going to try this now..brb :)

---

### Post by billytalent on 2009-01-19
This is the file : [http://daynite.deviantart.com/art/nUbuntu-GDM-Logins-75040717](http://daynite.deviantart.com/art/nUbuntu-GDM-Logins-75040717)

the brown one was activated :)

---

### Post by billytalent on 2009-01-19
Ok i found the problem and the solution from another user. It was written just below the gdm theme. 

> If the gdm loads forever, then here's the fix. Just copy the en translation file over to human theme.

sudo cp /usr/share/themes/Human/gtk-2.0/gtkrc /usr/share/themes/Human/gtk-2.0/gtkrc.en

The problem is that it loops until this file is available. something like:

Is the file available?
No
How about now?

or 

> I have found the solution:
Extract the themes and get rid of the gtk folder in both of them.
Copy in /usr/share/gdm/themes and then select them from the login window, then they will work fine. :))

Thing is, im in live CD at the mo and cant do anything...or can i? please tell me i can :(

---

### Post by billytalent on 2009-01-19
Fixed it myself, cheers mate :)

---

