---
title: "Help with start up"
date: 2006-02-05
forum: Desktop Environments
---

### Post by richardKitchen on 2006-02-05
How do get past start up after you have enbtered your password.

---

### Post by RAOF on 2006-02-05
What do you mean?  Where in this sequence do you have a problem?
You boot up Ubuntu.
You get to the login screen.  
You enter your username, followed by your password.  
The login screen disappears, and is replaced by your desktop wallpaper & a little splash-screen.
After a small period of time, everything is loaded, and you're ready to go.

And just as a general tip, you are ***much much*** more likely to receive an answer to a question if you give more information.  For example:
"I can't seem to get past start-up.  Ubuntu boots and displays no errors, then brings up the login screen.  After I enter my username & password and press enter, the login screen disappears and nothing further happens.  I've left it running for 5 minutes or so, still nothing."

---

### Post by richardKitchen on 2006-02-06
You get to the login screen. 
You enter your username, followed by your password. 
The login screen disappears,:Here is where I arun into a problem what I get is a screen that appears to be a terminal screen instead of being   replaced by your desktop wallpaper & a little splash-screen.
After a small period of time, everything is loaded, and you're ready to go.

---

### Post by RAOF on 2006-02-06
Ok.  So you end up at a terminal, with a prompt looking something like
```
chris@ubuntu:~$
```Yes?
And you can type stuff in, like "ls"<enter> and get some output?

Try typing "sudo /etc/init.d/gdm restart".  It will ask for a password.  Put in your own password.  It won't give any indication that you're putting in your password (no ***s or anything).  That should load the GUI.

---

### Post by richardKitchen on 2006-02-12
We I type in "sudo /etc/init.d/gdm restart". I get -bash: sudo /etc/init.d/gdm restart: No such file or directory
:confused:

---

### Post by Gandalf on 2006-02-12
With what you have installed ubuntu? server CD ?

---

### Post by richardKitchen on 2006-02-12
I installed from a CD that was in a linux magazine. I installed in as server

---

### Post by Gandalf on 2006-02-12
That's why there is no gdm :)

do
```

sudo apt-get install ubuntu-desktop

``` and you should be fine afterwards

---

### Post by richardKitchen on 2006-02-12
After I enter sudo apt-get install ubuntu-desktop  and I enter my password I got following:
reading package lists... done
building dependency tree ... done
ubuntu desktop is already the newest version.
0  upgrade, 0 newly installed, 0 to remove and 0 ungraded.
richard@richard:"$

---

