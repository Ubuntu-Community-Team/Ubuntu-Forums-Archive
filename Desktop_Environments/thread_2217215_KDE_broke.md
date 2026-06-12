---
title: "KDE broke"
date: 2014-04-16
forum: Desktop Environments
---

### Post by lunix2 on 2014-04-16
I had everything setup just as I wanted, then a false click of the mouse changed it all.  I have put most of it back, but some things are just broken:

When I did the click of death that broke everything (I don't know for sure what it was), my desktop icons were all gone.  The icons that I have put back on my desktop (e.g. Libre Office Writer, Muon Software Center, Dolphin) were all VERY big (I'd guess about 96x96).  I shrunk each of them, but can't get them to display text.

When I single click a desktop icon, it launches the app, even though double clicking (first click selects) is the selected option.

I can't move the desktop icons, even though they're unlocked.

I put a launcher on the panel associated with the taskbar near the Launcher menu button.  Then I deleted it.  But every time I login, it's there again.

I am using the Air theme (which is the default).

**NOTE:** I have another (administrative) user setup the way I want.  Can I just copy some files to get identical appearance and behavior for the root login (the one I broke)?

---

### Post by jmbell on 2014-04-16
Assuming you're not having trouble logging on or off, you might try deleting the .kde folder in your home directory, logging off and logging back in (or rebooting). This will erase your user settings; however, it would refresh kde at the same time. Having done this in the past myself, I can vouch that this folder is replaced on login if not present.

Before doing this, however, you might want to try running the following in a terminal (say, konsole):
```
 kwin --replace & 
```
This will reset the default window manager in kubuntu (kwin).

Hopefully this helps. Neither of these will upset the admin account you've set up.

---

### Post by lunix2 on 2014-04-16
Removing .KDE worked!!!  I can put it all back the way I want it and it stays.  But something else broke- the LibreOffice Writer launcher is gone,  All of the other LO launchers are where they should be.  How do I make one and replace it on the launch menu?


MANY thanks- I was utterly bewildered.

---

### Post by jmbell on 2014-04-16
The same thing happened to me a while back and I reinstalled the whole OS thinking the problem was rooted deeper in my system. Glad you didn't have to! :)

You might try running ```
 sudo apt-get install libreoffice-writer --reinstall 
``` Let me know what happens.

---

### Post by lunix2 on 2014-04-16
I found a way to add an appication launcher to the application launcher menu (right-click on the main launcher (what I call the start button)), then just copied most of the settings from calc.  It even has the right icon!

---

### Post by jmbell on 2014-04-16
Great! I wasn't exactly sure what you meant about the icon going missing. If it was a quick launch icon or something similar, you did the right thing. If you find the objects on your panel continue to move around (as mine did), you could try using the icon only task manager and the quicklaunch toolbar instead of individual icons for each program. That worked for me.

---

