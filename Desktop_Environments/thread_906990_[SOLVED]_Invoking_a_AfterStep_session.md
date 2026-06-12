---
title: "[SOLVED] Invoking a AfterStep session?"
date: 2008-09-01
forum: Desktop Environments
---

### Post by b9k9kiwi on 2008-09-01
Well, I've searched and searched for a simple 'how to' start/boot a session on an Ubuntu PC with AfterStep as the windows manager - I even searched the AfterStep site for at least a hint, but no luck.

I have downloaded the latest version of AfterStep, converted it to a .deb and installed it - but, now what?

help please:rolleyes:

---

### Post by kellemes on 2008-09-01
> **b9k9kiwi said:**
> Well, I've searched and searched for a simple 'how to' start/boot a session on an Ubuntu PC with AfterStep as the windows manager - I even searched the AfterStep site for at least a hint, but no luck.

I have downloaded the latest version of AfterStep, converted it to a .deb and installed it - but, now what?

help please:rolleyes:

I assume you still have GDM (your loginmanager) installed?
If so.. you can select Afterstep using the link/button "Sessions" in your loginscreen.

---

### Post by b9k9kiwi on 2008-09-01
> **kellemes said:**
> I assume you still have GDM (your loginmanager) installed?
If so.. you can select Afterstep using the link/button "Sessions" in your loginscreen.

Mmmm - AfterStep option is not available in login/sessions.  

Synaptic tells me that AfterStep 2.2.8 is installed, but maybe I have missed something somewhere in setup.  All I have done so far is run the .deb package installer having assumed that that was sufficient.

---

### Post by urukrama on 2008-09-01
If there is no After-step option in GDM (or whatever session manager you are using), you can easily create one.

The sessions are stored in /usr/share/xsessions

Create an empty text file there as root:

```
sudo nano /usr/share/xsessions/Afterstep.desktop
```

Add something like the following to it:

```
[Desktop Entry]
Encoding=UTF-8
Name=Afterstep
Comment=Login using the Afterstep session
**Exec=/usr/bin/afterstep**
Icon=
Type=XSession
```

Make sure that the Exec line (bold in the above example) matches the location where Afterstep is installed on your system. Type "whereis afterstep" in a terminal, and it will tell you where the binary is locate (usually /usr/bin/ or /usr/share/bin).

Make that file executable:

```
sudo chmod +x /usr/share/xsessions/Afterstep.desktop
```

Next time GDM starts you should see the Afterstep session (to restart GDM just press Ctrl+Alt+Backspace when you are at the login prompt, this will restart X, after which GDM should be restarted).

---

### Post by b9k9kiwi on 2008-09-02
> **urukrama said:**
> If there is no After-step option in GDM (or whatever session manager you are using), you can easily create one.

The sessions are stored in /usr/share/xsessions

...

Next time GDM starts you should see the Afterstep session (to restart GDM just press Ctrl+Alt+Backspace when you are at the login prompt, this will restart X, after which GDM should be restarted).

Something is awry in the AfterStep install it would seem, as your advice doesn't work for it.  No matter, because I installed Window Maker which subsequently appeared as a session option - and which, incidentally, I can't say really appeals to me (I was looking for something a la OS/2 & ObjectDesktop.

Anyway, thank you for your time - another element of Ubuntu/Linux which is no longer a mystery to me.

---

