---
title: "My Kde Panel Crashed!"
date: 2007-05-02
forum: Desktop Environments
---

### Post by linuxmann on 2007-05-02
This is strange. I am on my system prefs and all of a sudden my taskbar panel crashes. there is nothing on the bottom and i cannot access my programs, its all desktop. i tried restarting it and shutting it down the starting it up again but the panel will not show up whatsoever. HELP!

My taskbar is not showing up and i dont know what to do!

---

### Post by ComplexNumber on 2007-05-02
> **linuxmann said:**
> This is strange. I am on my system prefs and all of a sudden my taskbar panel crashes. there is nothing on the bottom and i cannot access my programs, its all desktop. i tried restarting it and shutting it down the starting it up again but the panel will not show up whatsoever. HELP!
how did you restart it and shut it down, exactly?

what you could try is this. go into the terminal and type in 'kcontrol' to bring up the kde control centre. go to Appearance, then Panel. there will be a switch there to make it autohide. try swiching between autohide and showing the panel.

---

### Post by linuxmann on 2007-05-02
I restarted it normally in the end session menu. But first i ended the current session. Restarting was the second thing i did. and a window showed up saying the panel has crashed. i dont know why it exactly did it but i need options how to bring it back. i think it could be a bug or a virus becaus i didnt have firestarter running.

I tried to change that option you were mentioning but it still will not show up.

EDIT: I unplugged my computers' power cord while it was off and then plugged it back in. then when i started it up again the panel was there.

---

### Post by ComplexNumber on 2007-05-02
> i think it could be a bug or a virus becaus i didnt have firestarter running.3 points:
a) its definitely not a virus :)
b) firestater is merely a frontend end for the actual firewall called iptables(or shorewall). it just allows you to configure it, thats all. the only time that you need to run firestarter is when you want to configure something.
c) you mention that you are running kde. firestarter is a gnome/gtk application, so it will look out of place on your desktop. the kde firewall frontend is called guarddog. its more configurable than firestarter, but is less intuitive.


i was going to mention that you should go to the terminal and type in 'killall kicker'. that will make it die, then restart.

---

### Post by venik212 on 2007-05-02
tt must be going around, since I just had the exact same crash.  I was told by some people to purge my system of kicker, and reinstall it.  That did revive the panels and menu, but something is missing-- I can no longer (auto)hide the panels at the bottom edge of the screen, and there is an error message, saying that a library is missing.  I tried purging and reinstalling kicker again, but the problem is still there.
I also lost the VERY NICE system setting menu that used to be on the panel.  I still have it in the K menu, but it is in a different, much less useful format.
Is there a way to bring  kicker back to life the way it used to be?

---

### Post by TooManyGames on 2007-05-20
I've been having the exact same problem with my kicker panel crashing.  First was on a Suse 10.2 install, now with my Kubuntu FF install.  It seems there's been a system update recently that's breaking something in KDE.  I've set my kicker panel to not auto-hide now, curious to know if it will still crash.

My suggestion is to keep a backup of your $KDEHOME/share/config/kickerrc file and when it crashes to replace that file and restart X (alt-ctrl-backspace).  Hopefully the KDE devs are aware of the issue and working on a fix.

---

