---
title: "Firefox installation trouble"
date: 2005-11-07
forum: Desktop Environments
---

### Post by MichaëlVD on 2005-11-07
I messed with my firefox 1.0.7 and 1.5 installs so much that nothing worked anymore. Therefore, I uninstalled everything and tried to install 1.0.7 again with sudo apt-get install firefox.

After doing that, running 'firefox' from the terminal does not work. Typing /usr/bin/firefox.ubuntu does, but I get this error in the terminal:

```
Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.*** loading the extensions datasource
Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.
```

Since firefox seems to be complaining about permissions, I try 'sudo /usr/bin/firefox.ubuntu'. This gives me the previous message and this:
```
You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.
*** loading the extensions datasource

```

Since  I had extension problems before, I would like to know what this means and how to solve it. Thanks!

---

### Post by RawMustard on 2005-11-07
Maybe you should look at this guide, it might help you to get Firefox 1.5 up and running which is much better than 1.07.  It's very easy to do, just follow the giude to the letter!

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by MichaëlVD on 2005-11-07
Thanks for your reply. In fact, I've tried that a few times before. It works now.

---

### Post by MichaëlVD on 2005-11-07
... hm, it only works if I start it with 'sudo firefox'

Looks like I still have a permission problem. Anyone?

---

### Post by RawMustard on 2005-11-07
What permissons are set on your firefox profile directory and it's files? You should be the owner of these!

---

### Post by MichaëlVD on 2005-11-07
Okay, I changed that (using sudo chown -R michael ~/.firefox/)

I also did sudo chmod -R 777 ~/.firefox/

~/.firefox$ ls -l gives me:

total 4
drwxrwxrwx  11 michael root 4096 2005-11-07 11:54 firefox

Typing 'sudo firefox' works, as before, 'firefox' doesn't...

'which firefox' gives '/usr/bin/firefox' and 'ls -l /usr/bin/firefox' gives:
lrwxrwxrwx  1 michael root 20 2005-11-07 13:24 /usr/bin/firefox -> /opt/firefox/firefox

The last thing I checked, 'ls -l /opt/firefox/firefox' gives:
-rwxrwxrwx  1 michael root 5239 2005-10-26 04:47 /opt/firefox/firefox

Quite bad that I still don't know how to solve a problem like this after more than 6 months of linux......

---

### Post by jrib on 2005-11-07
for the extensions problem, you can probably solve it be renaming your .mozilla folder in your home directory (be sure to backup your bookmarks file on your desktop so you can easily copy it to your new .mozilla folder).  When you run firefox again it will create a new .mozilla directory iirc.
(I tell you to rename it and not delete in case you need the files for whatever reason, better safe than sorry).

For the having to run firefox.ubuntu instead of just firefox, read the bottom of the firefoxNewVersion wiki.  It explains exactly what you should do when you remove firefox.

Here are the steps I would take if I were you,
1. follow the wiki for removing firefox 1.5 and do anything you forgot to do (it seems like you haven't removed the dpkg divert)
2. rename ~/.mozilla
3. run ff1.0.7
4. If that doesn't work, remove ff1.07 and install it again.
5. If that doesn't work, post here and we can probably work through it, good luck :D
6. Copy your bookmarks back to your new profile

---

### Post by MichaëlVD on 2005-11-07
The problem is solved, probably because I deleted ~/.mozilla/

I'm on 1.5 now.

thanks

---

