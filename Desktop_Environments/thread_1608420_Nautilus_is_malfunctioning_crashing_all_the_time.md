---
title: "Nautilus is malfunctioning: crashing all the time"
date: 2010-10-29
forum: Desktop Environments
---

### Post by ChrisBuchholz on 2010-10-29
Hey guys,

Yesterday, I was gonna try the gnome-shell version from the ppa on my 10.10 amd64 machine, so I installed it and then concluded that it was not new enough, and that I would just keep building gnome-shell my self from the git repository.
I did a ```
sudo apt-get purge gnome-shell
``` and then also an autoremove, because some packages was no longer used. After that, nautilus kept crashing.

I get a loading-cursor almost anywhere except for apps-content-places, I have no "desktop" - i cant see icons on it, cant right-click and so on, and I cant use nautilus to browse my files and folders. If I try to run nautilus from a terminal, I get this:
```
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 129 error_code 16 request_code 128 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I have tried to install gnome-shell again, since I figured it might removed some needed packages for nautilus. I have done a ```
sudo apt-get install --reinstall nautilus nautilus-data
``` to trick it to install nautilus again, but nothing fixes the problem.

Any idea to what can be wrong and how I fix it?

---

### Post by nilarimogard on 2010-10-29
Are you by any chance using RGBA transparency? If so, that might cause it.

---

### Post by ChrisBuchholz on 2010-10-29
> **nilarimogard said:**
> Are you by any chance using RGBA transparency? If so, that might cause it.

I dunno if I am? How do I know?
The thing is - It worked fine yesterday, until I install and uninstall gnome-shell from the ubuntu repositiories.

---

### Post by ChrisBuchholz on 2010-10-29
I am experiencing nautilus trying to restart all the time, because it crashes all the time - a loop, if you will. This affect almost full CPU usage even though I am only using a terminal and Google Chrome.

I would love to hear about a fix for this!

---

### Post by 3Miro on 2010-10-29
Are you still using Gnome-shell? Try disabling the desktop effects, this may help.

---

### Post by ChrisBuchholz on 2010-10-29
> **3Miro said:**
> Are you still using Gnome-shell? Try disabling the desktop effects, this may help.

I actually could not get gnome-shell to work. Neither from compiz nor metacity. Not from the repository - i have build it my self multiple times where it has worked fine. But this issue i have, is just compiz.

---

### Post by 3Miro on 2010-10-29
If there is a problem with Nautilus and apt-get purge doesn't help, then the issue is probably in the local settings of nautilus. The quickest way to check is to make a new user, log out and log in with the new user. If everything is working, then you can check the settings for the original user by "Ctr + F2" then type:
```
 gconf-editor 
```

You can also try to delete all nautilus files in 
```
 .gconf/apps/nautilus 
```
then logout and login.

---

### Post by ChrisBuchholz on 2010-10-29
> **3Miro said:**
> If there is a problem with Nautilus and apt-get purge doesn't help, then the issue is probably in the local settings of nautilus. The quickest way to check is to make a new user, log out and log in with the new user. If everything is working, then you can check the settings for the original user by "Ctr + F2" then type:
```
 gconf-editor 
```

You can also try to delete all nautilus files in 
```
 .gconf/apps/nautilus 
```
then logout and login.

That didnt work at all, unfortunately. I tried purge ubuntu-desktop package which includes nautilus and nautilus-data and then removing the folder ~/.gconf/apps/nautilus, but it didnt solve it.

---

### Post by NightwishFan on 2010-10-29
ubuntu-desktop package includes nothing. It is just a metapackage. Do what the user above said with gconf, and then also run this command:
```
rm -r .nautilus
```

Log out and back in.

---

