---
title: "Log Out = Black Screen"
date: 2009-08-17
forum: Desktop Environments
---

### Post by jlacroix on 2009-08-17
I am using Kubuntu Jaunty 64-bit with KDE 4.3 final. For some reason, I can log in and use my laptop just fine but whenever I log out I get a black screen. I cannot switch to a TTY or anything, the only way out of it is to hold down the power button and forcefully shut off my laptop. ALT+CTRL+Backspace doesn't work either. Does anyone know a fix for this?

---

### Post by Dave_Connor on 2009-08-17
Maybe a driver issue. Have you tried messing with driver section for your /etc/X11/xorg.conf file ?

---

### Post by arch0njw on 2009-08-17
> **jlacroix said:**
> I am using Kubuntu Jaunty 64-bit with KDE 4.3 final. For some reason, I can log in and use my laptop just fine but whenever I log out I get a black screen. I cannot switch to a TTY or anything, the only way out of it is to hold down the power button and forcefully shut off my laptop. ALT+CTRL+Backspace doesn't work either. Does anyone know a fix for this?

Does CTRL+ALT+F1 bring you to a CLI login?

If so, can you login?

If so, try the following command:  sudo /etc/init.d/kdm restart

... let me know what happens.

Sorry to sound so if-then-else... ;)  I'm warming up for the workday!  :D

---

### Post by jlacroix on 2009-08-17
> **arch0njw said:**
> Does CTRL+ALT+F1 bring you to a CLI login?

If so, can you login?

If so, try the following command:  sudo /etc/init.d/kdm restart

... let me know what happens.

Sorry to sound so if-then-else... ;)  I'm warming up for the workday!  :D

No, unfortunately CTRL+ALT+F1 doesn't do anything, neither does ALT+CTRL+Backspace. It's just a black screen, and I have to turn it off manually.

I did follow [this]("http://ubuntuforums.org/showthread.php?t=1130582") guide to fixing the Intel driver on my laptop, as the Jaunty Intel issues are pretty bad. :( Thankfully that howto fixed all my graphical issues but I wonder if it caused this issue to start happening?

---

### Post by arch0njw on 2009-08-18
I recommend filing a bug on launchpad about this.  This sounds like a pretty heavy issue that either someone there could help you or they might be able to redirect you to something like a Linux Intel forum.  My intent with asking you to file a bug is to get this into the system as an issue to be fixed.

Sorry I couldn't be of more assistance.

---

### Post by jlacroix on 2009-08-18
> **arch0njw said:**
> I recommend filing a bug on launchpad about this.  This sounds like a pretty heavy issue that either someone there could help you or they might be able to redirect you to something like a Linux Intel forum.  My intent with asking you to file a bug is to get this into the system as an issue to be fixed.

Sorry I couldn't be of more assistance.

Thank you. I did as you asked and the bug report can be found [here]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/415482").

---

### Post by JK3mp on 2009-08-18
I had exactly the same issue i reinstalled the drivers(ATI) and DISABLED compiz effects. Upon updateing though i was able to reenable compiz just fine.

---

