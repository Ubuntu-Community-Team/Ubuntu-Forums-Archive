---
title: "Can't stop gdm normally"
date: 2011-03-12
forum: Desktop Environments
---

### Post by Objekt on 2011-03-12
In Ubuntu 10.04, we're supposed to use the following command to stop the X server (assuming the usual Gnome desktop environment):

```
sudo service gdm stop
```

The problem is, this has never worked correctly for me.  I see a bunch of messages about things being shutdown, then it hangs.  I've waited up to several minutes for something to finally happen so I can log in to the command line, but nothing ever happens.

What I've always ended up doing is pressing Ctrl+Alt+F4 to switch to a different console.  I was then able to log in there and do stuff that required the X server to be shut down, such as installing Nvidia drivers.

Is that how it's supposed to work?  It doesn't seem right.

Can't post the error message where the command hangs, because obviously I have to be running the GUI to post here.  But I'll jot it down next time I try the command.

---

### Post by Krytarik on 2011-03-13
Your second sentence somewhat confuses me. You do switch to a console, e.g. with Ctrl+Alt+F1, and login there before you run the command, do you!?

---

### Post by Objekt on 2011-03-13
No, I run the command from an instance of Terminal.  Does it matter?

---

### Post by Krytarik on 2011-03-13
> **Objekt said:**
> No, I run the command from an instance of Terminal.  Does it matter?
LOL:p  Doing it that way is like trying to hack off your legs while you are standing!

---

### Post by Objekt on 2011-03-14
I fully expect the GUI to go away once I stop the GDM service.  I do not expect the system to get stuck on one of the shutdown steps.  Are you saying that is a feature, not a bug?

What I've done so far is, switch to a different console (e.g. Ctrl + Alt+ F1) after issuing the "stop" command, then log back in and run the Nvidia drivers installer from there.  It just seemed odd to me that the GDM stop process got "stuck."

---

### Post by Krytarik on 2011-03-14
Indeed, I would expect that it doesn't work, but it should of course rather output an error message and quit instead of trying and hanging itself then.

The correct, working way to stop GDM would be like this:
- logout of your session
- press Ctrl+Alt+F1
- login at the console
```
sudo service gdm stop
```To start it again, of course:
```
sudo service gdm start
```You will automatically get logged in to a new xsession then, based upon your current default xsession option.

But let me ask you another question: Are you trying to install the Nvidia manually with the installer from its website?

---

### Post by Objekt on 2011-05-13
Yes, I use the NVidia .run package.  It's worked the last couple of times I tried it.  

Considering this one "solved" because it's fine as long as I issue the "gdm stop" command from the correct console.  Somehow I missed the fact that you have 8 consoles (Ctrl + Alt + F1 through F8) to work with in Ubuntu.

I still get GUI lockups from time to time - not sure what's causing it.  Doesn't happen consistently enough to diagnose so far.

---

