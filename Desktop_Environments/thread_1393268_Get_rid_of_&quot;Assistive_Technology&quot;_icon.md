---
title: "Get rid of &quot;Assistive Technology&quot; icon"
date: 2010-01-29
forum: Desktop Environments
---

### Post by pooja on 2010-01-29
How do I get rid of this annoying Assistive Techonology icon in the system tray?

I was trying to change the Ubuntu 9.10 Karmic Koala login splash screen so I tried many methods I found on the web. None worked at the end I gave up. In one of those trials I followed a YouTube video that said to give the following command to the Terminal 

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Since then, this annoying icon appeared and I don't know how to send it off.
Also, everytime I shut down the system some error warning notice comes up on the black screen and the machine takes more time to turn on and completely shut down.
Can anyone undo what I messed up, please?

---

### Post by Tiede on 2010-02-04
I did the exact same thing to change my gdm background and ended up with the same. To remove the Assistive Technologies icon:
1. go to System->Preferences->Accessibility (translating from french here, but you'll recognize the icon ;) )
2. click on keyboard preferences (second button)
3. uncheck the box that reads "allow activation[...] by keyboard shortcuts. (first check box on the top)...

As to your other problem, I have no idea what it is.
But just to be on the safe side, try a ```
sudo dpkg --configure -a
``` at a terminal...

---

### Post by pooja on 2010-02-05
Tiede, Thank you so much! It worked just fine!
As to the error notice, I tried giving that command from Terminal. It didn't work. I'll try to jot down some details next time the machine prepares to shut down.
Thanks again!

---

