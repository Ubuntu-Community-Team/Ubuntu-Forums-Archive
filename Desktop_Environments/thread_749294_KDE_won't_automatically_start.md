---
title: "KDE won't automatically start"
date: 2008-04-08
forum: Desktop Environments
---

### Post by gulagarchipelago on 2008-04-08
I am currently running Kubuntu 7.10.  I recently installed KDE4 to try and test it out, but soon uninstalled it.  However, once I did so, K will no longer start automatically.  I have to log in at the command prompt and type 'start x' to get it to run. 

If I do 'cat /etc/X11/default-display-manager', it returns /usr/lib/kde4/bin/kdm

How can I reset that to be KDE3?  I've already uninstalled the KDE4 core package.

---

### Post by Whiffle on 2008-04-08
You could try editing that file, changing that location to the binary of kdm for kde3.  I'd give ya more info but I'm not in Linux right now.

---

### Post by gulagarchipelago on 2008-04-08
Hmm...Can anyone enlighten me as to which path to use for KDE3?  I don't want to use the wrong one and make KDE completely unusable.

---

### Post by Whiffle on 2008-04-08
my guess would be:

/usr/lib/kde3/bin/kdm

You can check if its there by looking in that directory, if so it should work.

---

### Post by gulagarchipelago on 2008-04-08
Very odd...there is no /bin directory.  I can only go as far as /usr/lib/kde3
I'm hoping the KDE3 installation did not get corrupted.

---

### Post by dbasener on 2008-04-08
I had the opposite, maybe, situation.  I installed, from updates, KDE4.  When I log in successfully, nothing displays - I still have the login splash.  When I jump out of X to a basic screen terminal, I can see a bunch of KDE processes running.  .xsession-errors are not helpful, to me anyway.

This was on a new login ID created just for the purpose of exploring KDE4.

When I put konqueror in the Autostart, it displayed.  I was able to start a terminal from there and even start the kicker.  The window manager appeared to be there because I could move windows around - they had borders.  But if I moved one the background never re-drew in the areas it passed through.  On the other hand, if I iconized it, the background **did** redraw, just where the window had been.

Going back to KDE3 was no problem.  I didn't uninstall 4 because both 3 and 4 show up on the login screen (I am using kdm for that).

I know this doesn't actually help you.  It is more my own call for help.

I suppose I could just wait for the official release, but I have no reason to think that the upgrade to that will produce better results.

Dave

---

### Post by Whiffle on 2008-04-08
You could try:

sudo updatedb
sudo locate kdm

---

### Post by gulagarchipelago on 2008-04-08
Running the 'locate kdm' command yields this entry: /etc/kde3/kdm

Wondering if that may be it.  I suppose I can try editing that file and if it doesn't work, I can put it back the way it was via command line.

---

### Post by Whiffle on 2008-04-08
Nope thats a config file, looks like your kdm is not installed.  

try

sudo apt-get install kdm

---

### Post by gulagarchipelago on 2008-04-08
apt-get install kdm returns:
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

If you want, I can pipe the output of 'sudo locate kdm' to a text file or something.

---

### Post by warp99 on 2008-04-08
Do the following:

```
sudo apt-get remove --purge kdm
```
when or if the prompt says to stop xserver go ahead and say yes, then:
```
sudo apt-get install kdm
```
and then:
```
sudo reboot
```

Purging will remove all of the kdm configuration files and install a default configuration. Then kdm should start properly as a service from /etc/init.d.

Edit:

Did you remove the entries from your sources.list for the kde4 repositories? If not remove them and 'sudo apt-get update' before purging kdm.

---

### Post by gulagarchipelago on 2008-04-08
Yeah I commented out the sources when I uninstalled KDE4.  Thanks for the advice; I will try it out later tonight.

---

