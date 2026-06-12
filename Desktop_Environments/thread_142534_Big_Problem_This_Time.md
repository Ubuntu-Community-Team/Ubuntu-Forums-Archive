---
title: "Big Problem This Time"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Lexicon on 2006-03-10
I was attempting to fix my touchpad's settings in the xorg.conf file, and now, after going through the Kubuntu startup screen, instead of leading to the graphical KDE login it goes to a command-line login.  I don't know jack about command line stuff, but I did manage to go in and change the xorg.conf file back to what it was before I messed around with it, but on reboots it still won't go into KDE.

I can't imagine how editing a touchpad setting would wreck KDE like that (earlier I messed it up to the point where everything was fine except that the touchpad didn't work, and I managed to fix that)--but I swear I did nothing else.

As I said, I don't know much about command-line stuff, so maybe there's a simple way from here to load up the graphical interface (and then set it to do it automatically after that), but I don't know how to do it.  Can anyone help me here?  I don't want to have to reinstall all this again (and, honestly, if this can happen from just attempting to fix a touchpad's settings, I don't know if i want to reinstall).

---

### Post by aysiu on 2006-03-10
Have you tried this? ```
sudo /etc/init.d/kdm restart
```

---

### Post by Lexicon on 2006-03-10
[QUOTE=aysiu]Have you tried this? ```
sudo /etc/init.d/kdm restart
```[/QUOTE]

I hadn't, but doing it just gives me a stopping/starting response with nothing else.  :(

---

### Post by Jucato on 2006-03-10
So when you do this (kdm restart), you just see the stopping/starting prompts? I doesn't put you into the graphical interface then throws you back to the command line (you should see your screen flicker for a bit).

If not, how about typing this:
```
startx
```
If in case you do get thrown out of the GUI, you might be able to see some messages as to why you are not logging in to the GUI.

---

### Post by Lexicon on 2006-03-10
[QUOTE=Fenyx]So when you do this (kdm restart), you just see the stopping/starting prompts? ... [/QUOTE]

No flicker.  Just the text.  When I do startx, this is what I get:
```

xauth: creating new authority file /home/myusername/.serverauth.8211

X: warning; process set to priority -1 instead of priority 0
giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

I tried again and got:

```
xauth: error in locking authority file home/myusername/.Xauthority
```

---

### Post by Lexicon on 2006-03-11
Woohoo!  I fixed it.  I noticed the thread "Accidental uninstall of desktop" and followed someone's suggestions there.  I think I did:

```

sudo apt-get install xserver-xorg
sudo apt-get install kubuntu-desktop

```

And ta-da!  I'm now a Kubuntu Breezy Badger 5.10 user again!  I was afraid that doing that stuff above would mess up all my nice customization, but nope, I'm good.  Thanks to everyone who tried to help.

---

